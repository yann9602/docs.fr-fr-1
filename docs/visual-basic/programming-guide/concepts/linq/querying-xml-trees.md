---
title: "Interrogation d’arborescences XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9b2aa1e4852657590449be3e297302bf41ba3e5d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="f2290-102">Interrogation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2290-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="f2290-103">Cette section fournit des exemples de requêtes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2290-103">This section provides examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>  
  
 <span data-ttu-id="f2290-104">Pour plus d’informations sur l’écriture [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] les requêtes, consultez [mise en route de LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="f2290-104">For more information about writing [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="f2290-105">Une fois que vous avez instancié une arborescence XML, l’écriture de requêtes est le moyen le plus efficace pour extraire des données de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="f2290-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="f2290-106">De plus, l'interrogation combinée à la construction fonctionnelle vous permet de générer un nouveau document XML qui possède une forme différente du document d'origine.</span><span class="sxs-lookup"><span data-stu-id="f2290-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2290-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f2290-107">In This Section</span></span>  
  
|<span data-ttu-id="f2290-108">Rubrique</span><span class="sxs-lookup"><span data-stu-id="f2290-108">Topic</span></span>|<span data-ttu-id="f2290-109">Description</span><span class="sxs-lookup"><span data-stu-id="f2290-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f2290-110">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2290-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="f2290-111">Fournit des exemples courants d’interrogation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="f2290-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="f2290-112">Projections et Transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2290-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="f2290-113">Fournit des exemples courants de projection à partir d’arborescences XML et de transformation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="f2290-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="f2290-114">Techniques de requêtes (LINQ to XML) avancées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2290-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="f2290-115">Fournit des techniques d'interrogation utiles dans les scénarios plus avancés.</span><span class="sxs-lookup"><span data-stu-id="f2290-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="f2290-116">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2290-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="f2290-117">Présente un certain nombre d’expressions XPath et leurs [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] équivalents.</span><span class="sxs-lookup"><span data-stu-id="f2290-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="f2290-118">Transformations fonctionnelles pures de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2290-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="f2290-119">Présente un petit didacticiel sur l'écriture des requêtes dans le style de programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="f2290-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2290-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2290-120">See Also</span></span>  
 <span data-ttu-id="f2290-121">[Guide de programmation (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f2290-121">[Programming Guide (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span></span>  
<span data-ttu-id="f2290-122"> [Mise en route de LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="f2290-122"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)</span></span>
