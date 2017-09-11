---
title: "Guide pratique pour déclencher les événements de la classe de base dans les classes dérivées (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: 24
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
ms.openlocfilehash: 13501f51a1e99eb6fb792a1c6abe5c7029cc020a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="84852-102">Guide pratique pour déclencher les événements de la classe de base dans les classes dérivées (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="84852-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="84852-103">L’exemple suivant montre la méthode standard employée pour déclarer des événements dans une classe de base pour qu’ils puissent être déclenchés à partir de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="84852-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="84852-104">Ce modèle est largement utilisé dans les classes Windows Forms de la bibliothèque de classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84852-104">This pattern is used extensively in Windows Forms classes in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library.</span></span>  
  
 <span data-ttu-id="84852-105">Lorsque vous créez une classe qui peut être utilisée comme classe de base pour d’autres classes, tenez compte du fait que les événements constituent un type spécial de délégué qui ne peut être appelé qu’à partir de la classe qui les a déclarés.</span><span class="sxs-lookup"><span data-stu-id="84852-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="84852-106">Les classes dérivées ne peuvent pas appeler directement les événements qui sont déclarés dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="84852-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="84852-107">Même si vous pouvez avoir besoin d’un événement qui ne peut être déclenché que par la classe de base, la plupart du temps, vous devez permettre à la classe dérivée d’appeler les événements de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="84852-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="84852-108">Pour ce faire, vous pouvez créer une méthode d’appel protégée dans la classe de base qui encapsule l’événement.</span><span class="sxs-lookup"><span data-stu-id="84852-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="84852-109">En appelant ou en substituant cette méthode d’appel, les classes dérivées peuvent appeler indirectement l’événement.</span><span class="sxs-lookup"><span data-stu-id="84852-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84852-110">Ne déclarez pas les événements virtuels dans une classe de base et substituez-les dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="84852-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="84852-111">Le compilateur C# ne gère pas correctement ce type d’événement et il n’est pas possible de prévoir si un abonné de l’événement dérivé s’abonnera à l’événement de classe de base.</span><span class="sxs-lookup"><span data-stu-id="84852-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84852-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="84852-112">Example</span></span>  
 <span data-ttu-id="84852-113">[!code-cs[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="84852-113">[!code-cs[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84852-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84852-114">See Also</span></span>  
 <span data-ttu-id="84852-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="84852-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="84852-116">[Événements](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="84852-116">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="84852-117">[Délégués](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="84852-117">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="84852-118">[Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="84852-118">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 [<span data-ttu-id="84852-119">Création de gestionnaires d’événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84852-119">Creating Event Handlers in Windows Forms</span></span>](https://msdn.microsoft.com/library/dacysss4.aspx)

