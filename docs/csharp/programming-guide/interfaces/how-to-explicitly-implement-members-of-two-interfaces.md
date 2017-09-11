---
title: "Guide pratique pour implémenter de manière explicite des membres de deux interfaces (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: 15
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
ms.openlocfilehash: 1446233793e3fd61f09d7da99f4f68cb7b3eabb8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="4c0be-102">Guide pratique pour implémenter de manière explicite des membres de deux interfaces (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="4c0be-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="4c0be-103">L’implémentation explicite d’une [interface](../../../csharp/language-reference/keywords/interface.md) permet également au programmeur d’implémenter deux interfaces qui ont les mêmes noms de membres et donnent à chaque membre d’interface une implémentation distincte.</span><span class="sxs-lookup"><span data-stu-id="4c0be-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="4c0be-104">L’exemple suivant affiche les dimensions d’une zone dans les unités de mesure à la fois métriques et britanniques.</span><span class="sxs-lookup"><span data-stu-id="4c0be-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="4c0be-105">La [classe](../../../csharp/language-reference/keywords/class.md) Box implémente deux interfaces, IEnglishDimensions et IMetricDimensions, qui représentent les différents systèmes de mesure.</span><span class="sxs-lookup"><span data-stu-id="4c0be-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="4c0be-106">Les deux interfaces ont des noms de membres identiques, Length et Width.</span><span class="sxs-lookup"><span data-stu-id="4c0be-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c0be-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="4c0be-107">Example</span></span>  
 <span data-ttu-id="4c0be-108">[!code-cs[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c0be-108">[!code-cs[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4c0be-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="4c0be-109">Robust Programming</span></span>  
 <span data-ttu-id="4c0be-110">Si vous souhaitez utiliser par défaut les unités de mesure britanniques, implémentez les méthodes Length et Width normalement, puis implémentez explicitement les méthodes Length et Width à partir de l’interface IMetricDimensions :</span><span class="sxs-lookup"><span data-stu-id="4c0be-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 <span data-ttu-id="4c0be-111">[!code-cs[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c0be-111">[!code-cs[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]</span></span>  
  
 <span data-ttu-id="4c0be-112">Dans ce cas, vous pouvez accéder aux unités de mesure britanniques à partir de l’instance de classe et accéder aux unités métriques à partir de l’instance d’interface :</span><span class="sxs-lookup"><span data-stu-id="4c0be-112">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 <span data-ttu-id="4c0be-113">[!code-cs[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c0be-113">[!code-cs[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0be-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c0be-114">See Also</span></span>  
 <span data-ttu-id="4c0be-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c0be-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4c0be-116">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c0be-116">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="4c0be-117">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c0be-117">[Interfaces](../../../csharp/programming-guide/interfaces/index.md) </span></span>  
 [<span data-ttu-id="4c0be-118">Comment : implémenter de manière explicite des membres d’interface</span><span class="sxs-lookup"><span data-stu-id="4c0be-118">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)

