---
title: "Comment : implémenter de manière explicite des membres de deux interfaces (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f0820328f037008c152b2e23071ae0ba8dba02bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="5e8e9-102">Comment : implémenter de manière explicite des membres de deux interfaces (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5e8e9-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="5e8e9-103">L’implémentation explicite d’une [interface](../../../csharp/language-reference/keywords/interface.md) permet également au programmeur d’implémenter deux interfaces qui ont les mêmes noms de membres et donnent à chaque membre d’interface une implémentation distincte.</span><span class="sxs-lookup"><span data-stu-id="5e8e9-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="5e8e9-104">L’exemple suivant affiche les dimensions d’une zone dans les unités de mesure à la fois métriques et britanniques.</span><span class="sxs-lookup"><span data-stu-id="5e8e9-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="5e8e9-105">La [classe](../../../csharp/language-reference/keywords/class.md) Box implémente deux interfaces, IEnglishDimensions et IMetricDimensions, qui représentent les différents systèmes de mesure.</span><span class="sxs-lookup"><span data-stu-id="5e8e9-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="5e8e9-106">Les deux interfaces ont des noms de membres identiques, Length et Width.</span><span class="sxs-lookup"><span data-stu-id="5e8e9-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e8e9-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="5e8e9-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5e8e9-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="5e8e9-108">Robust Programming</span></span>  
 <span data-ttu-id="5e8e9-109">Si vous souhaitez utiliser par défaut les unités de mesure britanniques, implémentez les méthodes Length et Width normalement, puis implémentez explicitement les méthodes Length et Width à partir de l’interface IMetricDimensions :</span><span class="sxs-lookup"><span data-stu-id="5e8e9-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="5e8e9-110">Dans ce cas, vous pouvez accéder aux unités de mesure britanniques à partir de l’instance de classe et accéder aux unités métriques à partir de l’instance d’interface :</span><span class="sxs-lookup"><span data-stu-id="5e8e9-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5e8e9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e8e9-111">See Also</span></span>  
 [<span data-ttu-id="5e8e9-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5e8e9-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5e8e9-113">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="5e8e9-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="5e8e9-114">Interfaces</span><span class="sxs-lookup"><span data-stu-id="5e8e9-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="5e8e9-115">Comment : implémenter de manière explicite des membres d’interface</span><span class="sxs-lookup"><span data-stu-id="5e8e9-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
