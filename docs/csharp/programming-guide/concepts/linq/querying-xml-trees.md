---
title: "Interrogation d’arborescences XML (C#)"
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
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4bad11434ed2610492854d5ec4a7a84bceb189f3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="87db0-102">Interrogation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="87db0-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="87db0-103">Cette section fournit des exemples de requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87db0-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="87db0-104">Pour plus d’informations sur l’écriture de requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], consultez [Bien démarrer avec LINQ en C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="87db0-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="87db0-105">Une fois que vous avez instancié une arborescence XML, l’écriture de requêtes est le moyen le plus efficace pour extraire des données de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="87db0-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="87db0-106">De plus, l'interrogation combinée à la construction fonctionnelle vous permet de générer un nouveau document XML qui possède une forme différente du document d'origine.</span><span class="sxs-lookup"><span data-stu-id="87db0-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87db0-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="87db0-107">In This Section</span></span>  
  
|<span data-ttu-id="87db0-108">Rubrique</span><span class="sxs-lookup"><span data-stu-id="87db0-108">Topic</span></span>|<span data-ttu-id="87db0-109">Description</span><span class="sxs-lookup"><span data-stu-id="87db0-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="87db0-110">Requêtes de base (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="87db0-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="87db0-111">Fournit des exemples courants d’interrogation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="87db0-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="87db0-112">Projections et transformations (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="87db0-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="87db0-113">Fournit des exemples courants de projection à partir d’arborescences XML et de transformation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="87db0-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="87db0-114">Techniques de requêtes avancées (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="87db0-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="87db0-115">Fournit des techniques d'interrogation utiles dans les scénarios plus avancés.</span><span class="sxs-lookup"><span data-stu-id="87db0-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="87db0-116">LINQ to XML pour les utilisateurs XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="87db0-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="87db0-117">Présente un certain nombre d’expressions XPath et leurs équivalents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87db0-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="87db0-118">Transformations fonctionnelles pures de données XML (C#)</span><span class="sxs-lookup"><span data-stu-id="87db0-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="87db0-119">Présente un petit didacticiel sur l'écriture des requêtes dans le style de programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="87db0-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87db0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87db0-120">See Also</span></span>  
 <span data-ttu-id="87db0-121">[Guide de programmation (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="87db0-121">[Programming Guide (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span></span>  
 [<span data-ttu-id="87db0-122">Bien démarrer avec LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="87db0-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

