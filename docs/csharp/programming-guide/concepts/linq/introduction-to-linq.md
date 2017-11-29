---
title: "Présentation de LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6fd14840cfffb1a59949251b26c168aada336de9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="5d813-102">Présentation de LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5d813-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="5d813-103">LINQ (Language-Integrated Query) est une nouveauté du .NET Framework 3.5 qui crée un pont entre le monde des objets et celui des données.</span><span class="sxs-lookup"><span data-stu-id="5d813-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="5d813-104">En règle générale, les requêtes de données sont exprimées comme de simples chaînes, sans vérification de type au moment de l’exécution, ni prise en charge IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5d813-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="5d813-105">En outre, vous devez apprendre un langage de requête différent pour chaque type de source de données : bases de données SQL, documents XML, services web, etc.</span><span class="sxs-lookup"><span data-stu-id="5d813-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="5d813-106">LINQ fait d’une *requête* une construction de langage de première classe en C#.</span><span class="sxs-lookup"><span data-stu-id="5d813-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="5d813-107">Vous pouvez écrire des requêtes pour des collections d’objets fortement typées à l’aide de mots clés de langage et d’opérateurs familiers.</span><span class="sxs-lookup"><span data-stu-id="5d813-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="5d813-108">Vous pouvez écrire des requêtes LINQ en C# pour des bases de données SQL Server, des documents XML, des jeux de données ADO.NET et toute collection d’objets prenant en charge <xref:System.Collections.IEnumerable> ou l’interface générique <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="5d813-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="5d813-109">La prise en charge LINQ est également fournie par des tierces parties pour de nombreux services web et autres implémentations de base de données.</span><span class="sxs-lookup"><span data-stu-id="5d813-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="5d813-110">Vous pouvez utiliser des requêtes LINQ dans de nouveaux projets, ou avec des requêtes non LINQ dans des projets existants.</span><span class="sxs-lookup"><span data-stu-id="5d813-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="5d813-111">La seule exigence est que le projet cible .NET Framework 3.5 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5d813-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="5d813-112">L’illustration suivante de Visual Studio montre une requête LINQ partiellement terminée, exécutée sur une base de données SQL Server, en C# et en Visual Basic, avec un contrôle de type complet et une prise en charge IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5d813-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="5d813-113">![Requête LINQ avec Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="5d813-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5d813-114">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5d813-114">Next Steps</span></span>  
 <span data-ttu-id="5d813-115">Pour plus d’informations sur LINQ, commencez par vous familiariser avec certains concepts de base expliqués dans la section de prise en main de [Bien démarrer avec LINQ en C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), puis lisez la documentation relative à la technologie LINQ qui vous intéresse :</span><span class="sxs-lookup"><span data-stu-id="5d813-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="5d813-116">Bases de données SQL Server : [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span><span class="sxs-lookup"><span data-stu-id="5d813-116">SQL Server databases: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span></span>  
  
-   <span data-ttu-id="5d813-117">Documents XML [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="5d813-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="5d813-118">Datasets ADO.NET [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="5d813-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="5d813-119">Collections, fichiers, chaînes .NET. : [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="5d813-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d813-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d813-120">See Also</span></span>  
 [<span data-ttu-id="5d813-121">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="5d813-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
