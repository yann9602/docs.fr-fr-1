---
title: "Guide pratique pour implémenter de manière explicite des membres d'interface (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
caps.latest.revision: 16
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
ms.openlocfilehash: 88b96c15f724ee5961c72917308138a045988225
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="88e16-102">Guide pratique pour implémenter de manière explicite des membres d'interface (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="88e16-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="88e16-103">Cet exemple déclare une [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions` et une classe `Box`, qui implémente de manière explicite les membres d’interface `getLength` et `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="88e16-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="88e16-104">Les membres sont accessibles via l’instance d’interface `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="88e16-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e16-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="88e16-105">Example</span></span>  
 <span data-ttu-id="88e16-106">[!code-cs[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="88e16-106">[!code-cs[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="88e16-107">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="88e16-107">Robust Programming</span></span>  
  
-   <span data-ttu-id="88e16-108">Notez que les lignes suivantes de la méthode `Main` sont commentées car elles produiraient des erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="88e16-108">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="88e16-109">Un membre d’interface qui est implémenté de façon explicite n’est pas accessible à partir d’une instance de [classe](../../../csharp/language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="88e16-109">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     <span data-ttu-id="88e16-110">[!code-cs[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="88e16-110">[!code-cs[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]</span></span>  
  
-   <span data-ttu-id="88e16-111">Notez également que les lignes suivantes de la méthode `Main` impriment correctement les dimensions de la zone, car les méthodes sont appelées à partir d’une instance de l’interface :</span><span class="sxs-lookup"><span data-stu-id="88e16-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     <span data-ttu-id="88e16-112">[!code-cs[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="88e16-112">[!code-cs[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e16-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88e16-113">See Also</span></span>  
 <span data-ttu-id="88e16-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="88e16-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="88e16-115">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="88e16-115">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="88e16-116">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="88e16-116">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 [<span data-ttu-id="88e16-117">Comment : implémenter de manière explicite des membres de deux interfaces</span><span class="sxs-lookup"><span data-stu-id="88e16-117">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)

