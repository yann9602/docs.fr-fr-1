---
title: "Implémentation d’interface explicite (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6baf985e8031e1e859d20570168222ca8f368eff
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="290c8-102">Implémentation d’interface explicite (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="290c8-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="290c8-103">Si une [classe](../../../csharp/language-reference/keywords/class.md) implémente deux interfaces qui contiennent un membre avec la même signature, l’implémentation de ce membre sur la classe a pour conséquence que les deux interfaces utilisent ce membre comme leur implémentation.</span><span class="sxs-lookup"><span data-stu-id="290c8-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="290c8-104">Dans l’exemple suivant, tous les appels à `Paint` appellent la même méthode.</span><span class="sxs-lookup"><span data-stu-id="290c8-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 <span data-ttu-id="290c8-105">[!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="290c8-105">[!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]</span></span>  
  
 <span data-ttu-id="290c8-106">Toutefois, si les deux membres d’[interface](../../../csharp/language-reference/keywords/interface.md) n’exécutent pas la même fonction, cela peut engendrer une implémentation incorrecte d’une interface ou des deux.</span><span class="sxs-lookup"><span data-stu-id="290c8-106">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="290c8-107">Il est possible d’implémenter un membre d’interface explicitement, en créant un membre de classe qui n’est appelé que via l’interface et qui est spécifique à cette interface.</span><span class="sxs-lookup"><span data-stu-id="290c8-107">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="290c8-108">Pour ce faire, vous devez nommer le membre de classe avec le nom de l’interface et un point.</span><span class="sxs-lookup"><span data-stu-id="290c8-108">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="290c8-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="290c8-109">For example:</span></span>  
  
 <span data-ttu-id="290c8-110">[!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="290c8-110">[!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]</span></span>  
  
 <span data-ttu-id="290c8-111">Le membre de classe `IControl.Paint` est disponible uniquement via l’interface `IControl` et `ISurface.Paint` est disponible uniquement via `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="290c8-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="290c8-112">Les deux implémentations de méthode sont distinctes, et aucune n’est directement disponible sur la classe.</span><span class="sxs-lookup"><span data-stu-id="290c8-112">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="290c8-113">Exemple :</span><span class="sxs-lookup"><span data-stu-id="290c8-113">For example:</span></span>  
  
 <span data-ttu-id="290c8-114">[!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="290c8-114">[!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]</span></span>  
  
 <span data-ttu-id="290c8-115">L’implémentation explicite est également utilisée pour résoudre les cas où deux interfaces déclarent chacune des membres différents du même nom, comme une propriété et une méthode :</span><span class="sxs-lookup"><span data-stu-id="290c8-115">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 <span data-ttu-id="290c8-116">[!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="290c8-116">[!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]</span></span>  
  
 <span data-ttu-id="290c8-117">Pour implémenter les deux interfaces, une classe doit utiliser l’implémentation explicite pour la propriété P, la méthode P, ou les deux, pour éviter une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="290c8-117">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="290c8-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="290c8-118">For example:</span></span>  
  
 <span data-ttu-id="290c8-119">[!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="290c8-119">[!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="290c8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="290c8-120">See Also</span></span>  
 <span data-ttu-id="290c8-121">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="290c8-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="290c8-122">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="290c8-122">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="290c8-123">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="290c8-123">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 [<span data-ttu-id="290c8-124">Héritage</span><span class="sxs-lookup"><span data-stu-id="290c8-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)

