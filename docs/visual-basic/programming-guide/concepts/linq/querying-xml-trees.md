---
title: "Interrogation d’arborescences XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1516cdc58effaa3e738210b948b43d7ed170890a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="3d8c2-102">Interrogation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="3d8c2-103">Cette section fournit des exemples de requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d8c2-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="3d8c2-104">Pour plus d’informations sur l’écriture [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] de requêtes, consultez [mise en route de LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="3d8c2-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="3d8c2-105">Une fois que vous avez instancié une arborescence XML, l’écriture de requêtes est le moyen le plus efficace pour extraire des données de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="3d8c2-106">De plus, l'interrogation combinée à la construction fonctionnelle vous permet de générer un nouveau document XML qui possède une forme différente du document d'origine.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d8c2-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3d8c2-107">In This Section</span></span>  
  
|<span data-ttu-id="3d8c2-108">Rubrique</span><span class="sxs-lookup"><span data-stu-id="3d8c2-108">Topic</span></span>|<span data-ttu-id="3d8c2-109">Description</span><span class="sxs-lookup"><span data-stu-id="3d8c2-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3d8c2-110">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="3d8c2-111">Fournit des exemples courants d’interrogation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="3d8c2-112">Projections et Transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="3d8c2-113">Fournit des exemples courants de projection à partir d’arborescences XML et de transformation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="3d8c2-114">Techniques de requêtes (LINQ to XML) avancées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="3d8c2-115">Fournit des techniques d'interrogation utiles dans les scénarios plus avancés.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="3d8c2-116">LINQ to XML pour les utilisateurs de XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="3d8c2-117">Présente un certain nombre d’expressions XPath et leurs équivalents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d8c2-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="3d8c2-118">Transformations fonctionnelles pures de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="3d8c2-119">Présente un petit didacticiel sur l'écriture des requêtes dans le style de programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="3d8c2-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d8c2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d8c2-120">See Also</span></span>  
 [<span data-ttu-id="3d8c2-121">Guide de programmation (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d8c2-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="3d8c2-122">Bien démarrer avec LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d8c2-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
