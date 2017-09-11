---
title: "Effectuer des jointures groupées"
description: "Guide pratique pour effectuer des jointures groupées."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0410c5f673e61f91c00a69cb1659e0d72852f128
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="perform-grouped-joins"></a><span data-ttu-id="02d0b-104">Effectuer des jointures groupées</span><span class="sxs-lookup"><span data-stu-id="02d0b-104">Perform grouped joins</span></span>

<span data-ttu-id="02d0b-105">La jointure groupée est utile pour produire des structures de données hiérarchiques.</span><span class="sxs-lookup"><span data-stu-id="02d0b-105">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="02d0b-106">Elle associe chaque élément de la première collection à un jeu d’éléments corrélés de la deuxième collection.</span><span class="sxs-lookup"><span data-stu-id="02d0b-106">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="02d0b-107">Par exemple, une classe ou une table de base de données relationnelle nommée `Student` peut contenir deux champs : `Id` et `Name`.</span><span class="sxs-lookup"><span data-stu-id="02d0b-107">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="02d0b-108">Une deuxième classe ou table de base de données relationnelle nommée `Course` peut contenir deux champs : `StudentId` et `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="02d0b-108">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="02d0b-109">Une jointure groupée de ces deux sources de données, basée sur les champs `Student.Id` et `Course.StudentId` correspondants, regroupe chaque `Student` avec une collection d’objets `Course` (qui peut être vide).</span><span class="sxs-lookup"><span data-stu-id="02d0b-109">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02d0b-110">Chaque élément de la première collection apparaît dans le jeu de résultats d’une jointure groupée, même si des éléments corrélés sont trouvés dans la deuxième collection.</span><span class="sxs-lookup"><span data-stu-id="02d0b-110">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="02d0b-111">Si aucun élément corrélé n’est trouvé, la séquence d’éléments corrélés pour cet élément est vide.</span><span class="sxs-lookup"><span data-stu-id="02d0b-111">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="02d0b-112">Le sélecteur de résultats a donc accès à chaque élément de la première collection.</span><span class="sxs-lookup"><span data-stu-id="02d0b-112">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="02d0b-113">Cela n’est pas le cas du sélecteur de résultats dans une jointure non groupée, qui ne peut pas accéder à des éléments de la première collection qui n’ont aucune correspondance dans la deuxième collection.</span><span class="sxs-lookup"><span data-stu-id="02d0b-113">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="02d0b-114">Le premier exemple de cette rubrique montre comment effectuer une jointure groupée.</span><span class="sxs-lookup"><span data-stu-id="02d0b-114">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="02d0b-115">Le deuxième exemple montre comment utiliser une jointure groupée pour créer des éléments XML.</span><span class="sxs-lookup"><span data-stu-id="02d0b-115">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02d0b-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="02d0b-116">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="02d0b-117">Exemple de jointure groupée</span><span class="sxs-lookup"><span data-stu-id="02d0b-117">Group join example</span></span>  
 <span data-ttu-id="02d0b-118">L’exemple suivant effectue une jointure groupée d’objets de types `Person` et `Pet` où `Person` correspond à la propriété `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="02d0b-118">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="02d0b-119">Contrairement à une jointure non groupée qui produirait une paire d’éléments pour chaque correspondance, la jointure groupée produit un seul objet résultant pour chaque élément de la première collection, qui est un objet `Person` dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="02d0b-119">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="02d0b-120">Les éléments correspondants de la deuxième collection, qui sont des objets `Pet` dans cet exemple, sont regroupés dans une collection.</span><span class="sxs-lookup"><span data-stu-id="02d0b-120">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="02d0b-121">Enfin, le sélecteur de résultats crée un type anonyme pour chaque correspondance qui se compose de `Person.FirstName` et d’une collection d’objets `Pet`.</span><span class="sxs-lookup"><span data-stu-id="02d0b-121">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 <span data-ttu-id="02d0b-122">[!code-cs[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="02d0b-122">[!code-cs[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="02d0b-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="02d0b-123">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="02d0b-124">Exemple de jointure groupée pour créer des éléments XLM</span><span class="sxs-lookup"><span data-stu-id="02d0b-124">Group join to create XML example</span></span>  
 <span data-ttu-id="02d0b-125">Les jointures groupées sont appropriées pour créer des éléments XML à l’aide de LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="02d0b-125">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="02d0b-126">L’exemple suivant est similaire à l’exemple précédent, sauf qu’au lieu de créer des types anonymes, le sélecteur de résultats crée des éléments XML qui représentent les objets joints.</span><span class="sxs-lookup"><span data-stu-id="02d0b-126">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 <span data-ttu-id="02d0b-127">[!code-cs[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="02d0b-127">[!code-cs[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="02d0b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02d0b-128">See also</span></span>  
 <span data-ttu-id="02d0b-129"><xref:System.Linq.Enumerable.Join%2A></span><span class="sxs-lookup"><span data-stu-id="02d0b-129"><xref:System.Linq.Enumerable.Join%2A></span></span>   
 <span data-ttu-id="02d0b-130"><xref:System.Linq.Enumerable.GroupJoin%2A></span><span class="sxs-lookup"><span data-stu-id="02d0b-130"><xref:System.Linq.Enumerable.GroupJoin%2A></span></span>   
 <span data-ttu-id="02d0b-131">[Effectuer des jointures internes](perform-inner-joins.md) </span><span class="sxs-lookup"><span data-stu-id="02d0b-131">[Perform inner joins](perform-inner-joins.md) </span></span>  
 <span data-ttu-id="02d0b-132">[Effectuer des jointures externes gauches](perform-left-outer-joins.md) </span><span class="sxs-lookup"><span data-stu-id="02d0b-132">[Perform left outer joins](perform-left-outer-joins.md) </span></span>  
 [<span data-ttu-id="02d0b-133">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="02d0b-133">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)   
 

