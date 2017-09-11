---
title: "Guide pratique pour implémenter des accesseurs d’événement personnalisés (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: 7
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
ms.openlocfilehash: 71e1c16c9c6426ffb95020e4d7211dc1000f6796
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="fb1e8-102">Guide pratique pour implémenter des accesseurs d’événement personnalisés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fb1e8-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="fb1e8-103">Un événement constitue un genre spécial de délégué multicast qui peut être appelé uniquement à partir de la classe dans laquelle il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="fb1e8-104">Le code client s’abonne à l’événement en fournissant une référence à une méthode qui doit être appelée quand l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="fb1e8-105">Ces méthodes sont ajoutées à la liste d’invocation du délégué par le biais des accesseurs d’événement, qui ressemblent aux accesseurs de propriété, sauf que les accesseurs d’événement sont nommés `add` et `remove`.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="fb1e8-106">Dans la plupart des cas, vous n’avez pas à fournir d’accesseurs d’événement personnalisés.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="fb1e8-107">Quand aucun accesseur d’événement personnalisé n’est fourni dans votre code, le compilateur les ajoute automatiquement.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="fb1e8-108">Toutefois, vous devez parfois fournir un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="fb1e8-109">Ce genre de cas est illustré dans la rubrique [Guide pratique pour implémenter des événements d’interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="fb1e8-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb1e8-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="fb1e8-110">Example</span></span>  
 <span data-ttu-id="fb1e8-111">L’exemple suivant indique comment implémenter des accesseurs d’événement add et remove.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="fb1e8-112">Même si vous pouvez remplacer le code à l’intérieur des accesseurs, nous vous recommandons de verrouiller l’événement avant d’ajouter ou de supprimer une nouvelle méthode de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="fb1e8-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb1e8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb1e8-113">See Also</span></span>  
 <span data-ttu-id="fb1e8-114">[Événements](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb1e8-114">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 [<span data-ttu-id="fb1e8-115">event</span><span class="sxs-lookup"><span data-stu-id="fb1e8-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)

