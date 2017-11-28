---
title: "Gérer des valeurs Null dans des expressions de requête"
description: "Comment gérer des valeurs Null dans des expressions de requête."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="2ba46-104">Gérer des valeurs Null dans des expressions de requête</span><span class="sxs-lookup"><span data-stu-id="2ba46-104">Handle null values in query expressions</span></span>

<span data-ttu-id="2ba46-105">Cet exemple montre comment gérer d’éventuelles valeurs Null dans des collections sources.</span><span class="sxs-lookup"><span data-stu-id="2ba46-105">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="2ba46-106">Une collection d’objets telle qu’un <xref:System.Collections.Generic.IEnumerable%601> peut contenir des éléments dont la valeur est [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="2ba46-106">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="2ba46-107">Si une collection source est null ou contient un élément dont la valeur est null et que votre requête ne gère pas les valeurs null, une <xref:System.NullReferenceException> est levée quand vous exécutez la requête.</span><span class="sxs-lookup"><span data-stu-id="2ba46-107">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ba46-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ba46-108">Example</span></span>

 <span data-ttu-id="2ba46-109">Vous pouvez écrire du code en prévention pour éviter une exception de référence Null, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="2ba46-109">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 <span data-ttu-id="2ba46-110">Dans l’exemple précédent, la clause `where` exclut tous les éléments Null de la séquence de catégories.</span><span class="sxs-lookup"><span data-stu-id="2ba46-110">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="2ba46-111">Cette technique est indépendante de la vérification de valeur Null de la clause join.</span><span class="sxs-lookup"><span data-stu-id="2ba46-111">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="2ba46-112">Dans cet exemple, l’expression conditionnelle avec une valeur Null fonctionne, car `Products.CategoryID` est de type `int?`, qui est le raccourci de `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="2ba46-112">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ba46-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ba46-113">Example</span></span>

 <span data-ttu-id="2ba46-114">Dans une clause join, si seulement l’une des clés de comparaison est un type valeur Nullable, vous pouvez caster l’autre clé en type Nullable dans l’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="2ba46-114">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="2ba46-115">Dans l’exemple suivant, supposons que `EmployeeID` soit une colonne qui contienne des valeurs de type `int?` :</span><span class="sxs-lookup"><span data-stu-id="2ba46-115">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2ba46-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ba46-116">See also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="2ba46-117">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="2ba46-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="2ba46-118">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="2ba46-118">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
