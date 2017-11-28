---
title: "Guide pratique pour retourner des sous-ensembles de propriétés d'éléments dans une requête (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6654b162fbdeb59ed2a135d7d8cf58c8b3406c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="6d2e0-102">Guide pratique pour retourner des sous-ensembles de propriétés d'éléments dans une requête (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6d2e0-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="6d2e0-103">Utilisez un type anonyme dans une expression de requête lorsque les deux conditions suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="6d2e0-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="6d2e0-104">Vous souhaitez retourner uniquement certaines propriétés de chaque élément source.</span><span class="sxs-lookup"><span data-stu-id="6d2e0-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="6d2e0-105">Vous n’avez pas besoin de stocker les résultats de requête en dehors de la portée de la méthode dans laquelle la requête est exécutée.</span><span class="sxs-lookup"><span data-stu-id="6d2e0-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="6d2e0-106">Si vous souhaitez uniquement retourner une propriété ou un champ de chaque élément source, vous pouvez utiliser l’opérateur point dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="6d2e0-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="6d2e0-107">Par exemple, pour retourner uniquement l’`ID` de chaque `student`, écrivez la clause `select` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="6d2e0-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="6d2e0-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d2e0-108">Example</span></span>  
 <span data-ttu-id="6d2e0-109">L’exemple suivant montre comment utiliser un type anonyme pour retourner uniquement un sous-ensemble des propriétés de chaque élément source qui répond à la condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6d2e0-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 <span data-ttu-id="6d2e0-110">Notez que le type anonyme utilise les noms de l’élément source pour ses propriétés si aucun nom n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6d2e0-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="6d2e0-111">Pour attribuer de nouveaux noms aux propriétés du type anonyme, écrivez l’instruction `select` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="6d2e0-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="6d2e0-112">Si vous effectuez cette opération dans l’exemple précédent, l’instruction `Console.WriteLine` doit également changer :</span><span class="sxs-lookup"><span data-stu-id="6d2e0-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d2e0-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6d2e0-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="6d2e0-114">Pour exécuter ce code, copiez et collez la classe dans un projet d’application console Visual C# qui a été créé dans [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d2e0-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="6d2e0-115">Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], et il comporte une référence à System.Core.dll et une directive `using` pour System.Linq.</span><span class="sxs-lookup"><span data-stu-id="6d2e0-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="6d2e0-116">Si un ou plusieurs de ces éléments sont manquants dans le projet, vous pouvez les ajouter manuellement.</span><span class="sxs-lookup"><span data-stu-id="6d2e0-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="6d2e0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d2e0-117">See Also</span></span>  
 [<span data-ttu-id="6d2e0-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6d2e0-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d2e0-119">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="6d2e0-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="6d2e0-120">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="6d2e0-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
