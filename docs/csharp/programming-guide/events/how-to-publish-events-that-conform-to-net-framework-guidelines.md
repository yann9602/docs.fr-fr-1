---
title: "Guide pratique pour publier des événements conformes aux indications du .NET Framework (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 21badd504a54c7000fef76e901cc952134eff61e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="c798c-102">Guide pratique pour publier des événements conformes aux indications du .NET Framework (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c798c-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="c798c-103">La procédure suivante montre comment ajouter à vos classes et structs des événements qui respectent le modèle [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] standard.</span><span class="sxs-lookup"><span data-stu-id="c798c-103">The following procedure demonstrates how to add events that follow the standard [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern to your classes and structs.</span></span> <span data-ttu-id="c798c-104">Tous les événements de la bibliothèque de classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sont basés sur le délégué <xref:System.EventHandler>, qui est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="c798c-104">All events in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  <span data-ttu-id="c798c-105">Le [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] introduit une version générique de ce délégué : <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="c798c-105">The [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="c798c-106">Les exemples suivants montrent comment utiliser les deux versions.</span><span class="sxs-lookup"><span data-stu-id="c798c-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="c798c-107">Bien que les événements des classes que vous définissez puissent être basés sur n’importe quel type délégué valide, même les délégués qui retournent une valeur, il est généralement recommandé de baser les événements sur le modèle [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] à l’aide de <xref:System.EventHandler>, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c798c-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="c798c-108">Pour publier des événements basés sur le modèle EventHandler</span><span class="sxs-lookup"><span data-stu-id="c798c-108">To publish events based on the EventHandler pattern</span></span>  
  
1.  <span data-ttu-id="c798c-109">(Ignorez cette étape et passez à l’étape 3a si vous n’avez pas à envoyer de données personnalisées avec votre événement.) Déclarez la classe pour vos données personnalisées avec une étendue visible par vos classes de serveur de publication et d’abonné.</span><span class="sxs-lookup"><span data-stu-id="c798c-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="c798c-110">Ajoutez ensuite les membres nécessaires pour contenir vos données d’événement personnalisées.</span><span class="sxs-lookup"><span data-stu-id="c798c-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="c798c-111">Dans cet exemple, une simple chaîne est retournée.</span><span class="sxs-lookup"><span data-stu-id="c798c-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2.  <span data-ttu-id="c798c-112">(Ignorez cette étape si vous utilisez la version générique de <xref:System.EventHandler%601>.) Déclarez un délégué dans votre classe de publication.</span><span class="sxs-lookup"><span data-stu-id="c798c-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="c798c-113">Donnez-lui un nom qui se termine par *EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="c798c-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="c798c-114">Le deuxième paramètre spécifie votre type EventArgs personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c798c-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  <span data-ttu-id="c798c-115">Déclarez l’événement dans votre classe de publication en effectuant l’une des étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c798c-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1.  <span data-ttu-id="c798c-116">Si vous n’avez aucune classe EventArgs personnalisée, votre type d’événement sera le délégué EventHandler non générique.</span><span class="sxs-lookup"><span data-stu-id="c798c-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="c798c-117">Il est inutile de déclarer le délégué, car il l’est déjà dans l’espace de noms <xref:System> inclus au moment où vous créez votre projet C#.</span><span class="sxs-lookup"><span data-stu-id="c798c-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="c798c-118">Ajoutez le code suivant à votre classe de serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="c798c-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  <span data-ttu-id="c798c-119">Si vous utilisez la version non générique de <xref:System.EventHandler> et que vous avez une classe personnalisée dérivée de <xref:System.EventArgs>, déclarez votre événement à l’intérieur de votre classe de publication et utilisez votre délégué de l’étape 2 comme type.</span><span class="sxs-lookup"><span data-stu-id="c798c-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  <span data-ttu-id="c798c-120">Si vous utilisez la version générique, vous n’avez pas besoin de délégué personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c798c-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="c798c-121">Au lieu de cela, dans votre classe de publication, vous spécifiez votre type d’événement en tant que `EventHandler<CustomEventArgs>`, en insérant le nom de votre propre classe entre les crochets.</span><span class="sxs-lookup"><span data-stu-id="c798c-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="c798c-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="c798c-122">Example</span></span>  
 <span data-ttu-id="c798c-123">L’exemple suivant est une illustration des étapes précédentes avec l’utilisation d’une classe EventArgs personnalisée et de <xref:System.EventHandler%601> comme type d’événement.</span><span class="sxs-lookup"><span data-stu-id="c798c-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 <span data-ttu-id="c798c-124">[!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c798c-124">[!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c798c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c798c-125">See Also</span></span>  
 <span data-ttu-id="c798c-126"><xref:System.Delegate></span><span class="sxs-lookup"><span data-stu-id="c798c-126"><xref:System.Delegate></span></span>   
 <span data-ttu-id="c798c-127">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c798c-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c798c-128">[Événements](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="c798c-128">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 [<span data-ttu-id="c798c-129">Délégués</span><span class="sxs-lookup"><span data-stu-id="c798c-129">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

