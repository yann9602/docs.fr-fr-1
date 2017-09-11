---
title: "Filtrage des données (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: defa6716f677c44da5dd27cb64b3b1d140a65272
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="filtering-data-c"></a><span data-ttu-id="a8a61-102">Filtrage des données (C#)</span><span class="sxs-lookup"><span data-stu-id="a8a61-102">Filtering Data (C#)</span></span>
<span data-ttu-id="a8a61-103">Le filtrage fait référence à l’opération de restriction du jeu de résultats pour que celui-ci contienne uniquement les éléments qui répondent à une condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a8a61-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="a8a61-104">Cette opération est également appelée « sélection ».</span><span class="sxs-lookup"><span data-stu-id="a8a61-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="a8a61-105">L’illustration suivante montre les résultats du filtrage d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="a8a61-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="a8a61-106">Le prédicat de l’opération de filtrage spécifie que le caractère doit être « A ».</span><span class="sxs-lookup"><span data-stu-id="a8a61-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="a8a61-107">![Opération de filtrage LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="a8a61-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="a8a61-108">Les méthodes d’opérateurs de requête standard qui effectuent des opérations de sélection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="a8a61-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8a61-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a8a61-109">Methods</span></span>  
  
|<span data-ttu-id="a8a61-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="a8a61-110">Method Name</span></span>|<span data-ttu-id="a8a61-111">Description</span><span class="sxs-lookup"><span data-stu-id="a8a61-111">Description</span></span>|<span data-ttu-id="a8a61-112">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="a8a61-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="a8a61-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="a8a61-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="a8a61-114">OfType</span><span class="sxs-lookup"><span data-stu-id="a8a61-114">OfType</span></span>|<span data-ttu-id="a8a61-115">Sélectionne des valeurs, en fonction de leur capacité à être castées en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="a8a61-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="a8a61-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="a8a61-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|<span data-ttu-id="a8a61-117">Où</span><span class="sxs-lookup"><span data-stu-id="a8a61-117">Where</span></span>|<span data-ttu-id="a8a61-118">Sélectionne les valeurs qui sont basées sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="a8a61-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="a8a61-119">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="a8a61-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="a8a61-120">L’exemple suivant utilise la clause `where` pour filtrer les chaînes d’un tableau qui ont une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="a8a61-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8a61-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8a61-121">See Also</span></span>  
 <span data-ttu-id="a8a61-122"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="a8a61-122"><xref:System.Linq></span></span>   
 <span data-ttu-id="a8a61-123">[Présentation des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="a8a61-123">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="a8a61-124">[where, clause](../../../../csharp/language-reference/keywords/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="a8a61-124">[where clause](../../../../csharp/language-reference/keywords/where-clause.md) </span></span>  
 <span data-ttu-id="a8a61-125">[Guide pratique pour spécifier dynamiquement des filtres de prédicat au moment de l’exécution](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span><span class="sxs-lookup"><span data-stu-id="a8a61-125">[How to: Dynamically Specify Predicate Filters at Runtime](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span></span>  
 <span data-ttu-id="a8a61-126">[Guide pratique pour interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span><span class="sxs-lookup"><span data-stu-id="a8a61-126">[How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span></span>  
 <span data-ttu-id="a8a61-127">[Guide pratique pour interroger des fichiers ayant un attribut ou un nom donné (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span><span class="sxs-lookup"><span data-stu-id="a8a61-127">[How to: Query for Files with a Specified Attribute or Name (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span></span>  
 [<span data-ttu-id="a8a61-128">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a8a61-128">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

