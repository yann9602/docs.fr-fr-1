---
title: "Guide pratique pour implémenter des événements d'interface (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: 21
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
ms.openlocfilehash: 8f8460674aa59170cf75eb2fa93e9d232df07e5e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="379b0-102">Guide pratique pour implémenter des événements d'interface (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="379b0-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="379b0-103">Une [interface](../../../csharp/language-reference/keywords/interface.md) peut déclarer un [événement](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="379b0-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="379b0-104">L’exemple suivant montre comment implémenter des événements d’interface dans une classe.</span><span class="sxs-lookup"><span data-stu-id="379b0-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="379b0-105">En gros, les règles sont les mêmes que quand vous implémentez une propriété ou une méthode d’interface.</span><span class="sxs-lookup"><span data-stu-id="379b0-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
### <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="379b0-106">Pour implémenter des événements d’interface dans une classe</span><span class="sxs-lookup"><span data-stu-id="379b0-106">To implement interface events in a class</span></span>  
  
-   <span data-ttu-id="379b0-107">Déclarez l’événement dans votre classe, puis appelez-le aux emplacements appropriés.</span><span class="sxs-lookup"><span data-stu-id="379b0-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
    ```  
    namespace ImplementInterfaceEvents  
    {  
        public interface IDrawingObject  
        {  
            event EventHandler ShapeChanged;  
        }  
        public class MyEventArgs : EventArgs   
        {  
            // class members  
        }  
        public class Shape : IDrawingObject  
        {  
            public event EventHandler ShapeChanged;  
            void ChangeShape()  
            {  
                // Do something here before the event…  
  
                OnShapeChanged(new MyEventArgs(/*arguments*/));  
  
                // or do something here after the event.   
            }  
            protected virtual void OnShapeChanged(MyEventArgs e)  
            {  
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="379b0-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="379b0-108">Example</span></span>  
 <span data-ttu-id="379b0-109">L’exemple suivant montre comment gérer la situation peu courante dans laquelle votre classe hérite de plusieurs interfaces et chaque interface a un événement ayant le même nom.</span><span class="sxs-lookup"><span data-stu-id="379b0-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="379b0-110">Dans ce cas, vous devez fournir une implémentation d’interface explicite pour au moins l’un des événements.</span><span class="sxs-lookup"><span data-stu-id="379b0-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="379b0-111">Quand vous écrivez une implémentation d’interface explicite pour un événement, vous devez également écrire les accesseurs d’événement `add` et `remove`.</span><span class="sxs-lookup"><span data-stu-id="379b0-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="379b0-112">Normalement, ces éléments sont fournis par le compilateur, mais dans le cas en question le compilateur ne peut pas les fournir.</span><span class="sxs-lookup"><span data-stu-id="379b0-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
 <span data-ttu-id="379b0-113">En fournissant vos propres accesseurs, vous pouvez spécifier si les deux événements sont représentés par le même événement dans votre classe ou par des événements différents.</span><span class="sxs-lookup"><span data-stu-id="379b0-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="379b0-114">Par exemple, si les événements doivent être déclenchés à des moments différents en fonction des spécifications de l’interface, vous pouvez associer chaque événement à une implémentation distincte dans votre classe.</span><span class="sxs-lookup"><span data-stu-id="379b0-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="379b0-115">Dans l’exemple suivant, les abonnés déterminent l’événement `OnDraw` qu’il recevront en effectuant un cast de la référence de la forme en `IShape` ou `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="379b0-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 <span data-ttu-id="379b0-116">[!code-cs[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="379b0-116">[!code-cs[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="379b0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="379b0-117">See Also</span></span>  
 <span data-ttu-id="379b0-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="379b0-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="379b0-119">[Événements](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="379b0-119">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="379b0-120">[Délégués](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="379b0-120">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="379b0-121">[Implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="379b0-121">[Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) </span></span>  
 [<span data-ttu-id="379b0-122">Comment : déclencher les événements de la classe de base dans les classes dérivées</span><span class="sxs-lookup"><span data-stu-id="379b0-122">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)

