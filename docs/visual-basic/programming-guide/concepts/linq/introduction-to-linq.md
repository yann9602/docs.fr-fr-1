---
title: "Introduction à LINQ (Visual Basic) | Documents Microsoft"
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
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d2c02daacc2674da31715e5fda027b97e6b7bc97
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="1d4dc-102">Introduction à LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d4dc-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="1d4dc-103">Language-Integrated Query (LINQ) est qu'une innovation dans le .NET Framework version 3.5 qui permet l’écart entre le monde des objets et le monde des données.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="1d4dc-104">En règle générale, les requêtes sur les données sont exprimées compiler les chaînes simples sans vérification de type au moment ou la prise en charge IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="1d4dc-105">En outre, vous devez apprendre un langage de requête différente pour chaque type de source de données : SQL bases de données, documents XML, divers services Web et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="1d4dc-106">LINQ permet une *requête* une construction de langage de premier ordre en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="1d4dc-107">Vous écrivez des requêtes sur des collections fortement typées d’objets à l’aide de mots clés du langage et des opérateurs familiers.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="1d4dc-108">Vous pouvez écrire des requêtes LINQ en Visual Basic pour SQL Server bases de données XML des documents, des groupes de données ADO.NET et toute collection d’objets qui prend en charge <xref:System.Collections.IEnumerable>ou générique <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="1d4dc-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="1d4dc-109">Prise en charge LINQ est également fournie par des tiers pour de nombreux services Web et d’autres implémentations de base de données.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="1d4dc-110">Vous pouvez utiliser des requêtes LINQ dans les nouveaux projets ou avec des requêtes non-LINQ dans des projets existants.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="1d4dc-111">La seule exigence est que le projet cible .NET Framework 3.5 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="1d4dc-112">L’illustration suivante à partir de Visual Studio affiche une requête LINQ partiellement terminée sur une base de données SQL Server dans les langages c# et Visual Basic avec vérification de type complet et la prise en charge IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="1d4dc-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="1d4dc-113">![Requête LINQ avec Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="1d4dc-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1d4dc-114">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1d4dc-114">Next Steps</span></span>  
 <span data-ttu-id="1d4dc-115">Pour en savoir plus sur LINQ, commencez par vous familiariser avec certains concepts de base dans la section mise en route [mise en route de LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), puis lisez la documentation de la technologie LINQ qui vous intéresse :</span><span class="sxs-lookup"><span data-stu-id="1d4dc-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="1d4dc-116">Bases de données SQL Server : [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span><span class="sxs-lookup"><span data-stu-id="1d4dc-116">SQL Server databases: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span></span>  
  
-   <span data-ttu-id="1d4dc-117">Documents XML : [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="1d4dc-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="1d4dc-118">Groupes de données ADO.NET : [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)</span><span class="sxs-lookup"><span data-stu-id="1d4dc-118">ADO.NET Datasets: [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)</span></span>  
  
-   <span data-ttu-id="1d4dc-119">Collections .NET, fichiers, chaînes et ainsi de suite : [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="1d4dc-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d4dc-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d4dc-120">See Also</span></span>  
 [<span data-ttu-id="1d4dc-121">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d4dc-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
