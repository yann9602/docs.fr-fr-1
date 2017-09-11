---
title: "LINQ et chaînes (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 94e9627efb183c08bbb67a7e6e82df9132ebdef2
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="8765c-102">LINQ et chaînes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="8765c-103">LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes.</span><span class="sxs-lookup"><span data-stu-id="8765c-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="8765c-104">Il peut être particulièrement utile avec les données semi-structurées dans les fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="8765c-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="8765c-105">Les requêtes LINQ peuvent être combinées avec les fonctions de chaîne traditionnelles et les expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="8765c-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="8765c-106">Par exemple, vous pouvez utiliser la <xref:System.String.Split%2A>ou <xref:System.Text.RegularExpressions.Regex.Split%2A>pour créer un tableau de chaînes que vous pouvez ensuite interroger ou modifier en utilisant LINQ.</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="8765c-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="8765c-107">Vous pouvez utiliser la <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>méthode dans le `where` clause d’une requête LINQ.</xref:System.Text.RegularExpressions.Regex.IsMatch%2A></span><span class="sxs-lookup"><span data-stu-id="8765c-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="8765c-108">Et vous pouvez utiliser LINQ pour interroger ou modifier le <xref:System.Text.RegularExpressions.MatchCollection>les résultats retournés par une expression régulière.</xref:System.Text.RegularExpressions.MatchCollection></span><span class="sxs-lookup"><span data-stu-id="8765c-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="8765c-109">Vous pouvez également utiliser les techniques décrites dans cette section pour transformer des données de texte semi-structurées en XML.</span><span class="sxs-lookup"><span data-stu-id="8765c-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="8765c-110">Pour plus d’informations, consultez [Comment : générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="8765c-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="8765c-111">Les exemples de cette section se répartissent en deux catégories :</span><span class="sxs-lookup"><span data-stu-id="8765c-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="8765c-112">Interrogation d’un bloc de texte</span><span class="sxs-lookup"><span data-stu-id="8765c-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="8765c-113">Vous pouvez interroger, analyser et modifier des blocs de texte en les fractionnant en un tableau requêtable de plus petites chaînes à l’aide de la <xref:System.String.Split%2A>méthode ou <xref:System.Text.RegularExpressions.Regex.Split%2A>méthode.</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="8765c-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="8765c-114">Vous pouvez fractionner le texte source en mots, phrases, paragraphes, pages ou d’autres critères et puis effectuer des fractionnements supplémentaires s’ils sont requis dans votre requête.</span><span class="sxs-lookup"><span data-stu-id="8765c-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="8765c-115">Comment : compter les Occurrences d’un mot dans une chaîne (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="8765c-116">Montre comment utiliser LINQ pour les interrogations simples sur le texte.</span><span class="sxs-lookup"><span data-stu-id="8765c-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="8765c-117">Comment : rechercher des phrases qui contiennent un jeu spécifié de mots (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="8765c-118">Montre comment fractionner des fichiers texte avec des limites arbitraires et comment exécuter des requêtes sur chaque partie.</span><span class="sxs-lookup"><span data-stu-id="8765c-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="8765c-119">Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="8765c-120">Montre qu’une chaîne est un type requêtable.</span><span class="sxs-lookup"><span data-stu-id="8765c-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="8765c-121">Comment : combiner des requêtes LINQ avec des Expressions régulières (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="8765c-122">Montre comment utiliser des expressions régulières dans les requêtes LINQ pour les critères spéciaux complexes sur les résultats de requête filtrée.</span><span class="sxs-lookup"><span data-stu-id="8765c-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="8765c-123">Interrogation des données semi-structurées au Format texte</span><span class="sxs-lookup"><span data-stu-id="8765c-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="8765c-124">Différents types de fichiers texte sont constitués d’une série de lignes, généralement avec la même mise en forme, telles que les fichiers délimité par des tabulations ou des virgules ou des lignes de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="8765c-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="8765c-125">Après avoir lu un tel fichier texte dans la mémoire, vous pouvez utiliser LINQ pour interroger et/ou modifier les lignes.</span><span class="sxs-lookup"><span data-stu-id="8765c-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="8765c-126">Requêtes LINQ simplifient également la combinaison des données provenant de plusieurs sources.</span><span class="sxs-lookup"><span data-stu-id="8765c-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="8765c-127">Comment : rechercher la différence définie entre deux listes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="8765c-128">Montre comment rechercher toutes les chaînes qui sont présents dans une liste, mais pas l’autre.</span><span class="sxs-lookup"><span data-stu-id="8765c-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="8765c-129">Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="8765c-130">Montre comment trier les lignes de texte en fonction de n’importe quel mot ou le champ.</span><span class="sxs-lookup"><span data-stu-id="8765c-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="8765c-131">Comment : réorganiser les champs d’un fichier délimité (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="8765c-132">Montre comment réorganiser les champs dans une ligne dans un fichier .csv.</span><span class="sxs-lookup"><span data-stu-id="8765c-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="8765c-133">Comment : combiner et comparer des Collections de chaînes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="8765c-134">Montre comment combiner des listes de chaîne de différentes manières.</span><span class="sxs-lookup"><span data-stu-id="8765c-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="8765c-135">Comment : remplir des Collections d’objets issues de plusieurs Sources (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="8765c-136">Montre comment créer des collections d’objets à l’aide de plusieurs fichiers texte comme sources de données.</span><span class="sxs-lookup"><span data-stu-id="8765c-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="8765c-137">Comment : joindre du contenu issu de différents fichiers (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="8765c-138">Montre comment combiner des chaînes dans deux listes en une seule chaîne à l’aide d’une clé correspondante.</span><span class="sxs-lookup"><span data-stu-id="8765c-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="8765c-139">Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="8765c-140">Montre comment créer des fichiers à l’aide d’un seul fichier comme source de données.</span><span class="sxs-lookup"><span data-stu-id="8765c-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="8765c-141">Comment : calculer des valeurs de colonne dans un fichier de texte CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8765c-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="8765c-142">Montre comment effectuer des calculs mathématiques sur des données texte dans des fichiers .csv.</span><span class="sxs-lookup"><span data-stu-id="8765c-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8765c-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8765c-143">See Also</span></span>  
 <span data-ttu-id="8765c-144">[Language-Integrated Query (LINQ) (Visual Basic)](index.md) </span><span class="sxs-lookup"><span data-stu-id="8765c-144">[Language-Integrated Query (LINQ) (Visual Basic)](index.md) </span></span>  
<span data-ttu-id="8765c-145"> [Guide pratique : générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md)</span><span class="sxs-lookup"><span data-stu-id="8765c-145"> [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md)</span></span>

