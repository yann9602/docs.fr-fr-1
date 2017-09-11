---
title: Projections et Transformations (LINQ to XML) (Visual Basic) | Documents Microsoft
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
ms.assetid: 297de224-b625-44cf-8c00-186b6189aa0e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 723685400aadbf883d7ad939e6a1dd5bdeb7ba09
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="projections-and-transformations-linq-to-xml-visual-basic"></a><span data-ttu-id="29acc-102">Projections et Transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-102">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="29acc-103">Cette section fournit des exemples de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] projections et transformations.</span><span class="sxs-lookup"><span data-stu-id="29acc-103">This section provides examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="29acc-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="29acc-104">In This Section</span></span>  
  
|<span data-ttu-id="29acc-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="29acc-105">Topic</span></span>|<span data-ttu-id="29acc-106">Description</span><span class="sxs-lookup"><span data-stu-id="29acc-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="29acc-107">Comment : travailler avec des dictionnaires à l’aide de LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-107">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="29acc-108">Montre comment transformer des dictionnaires au format XML et comment transformer du code XML en dictionnaires.</span><span class="sxs-lookup"><span data-stu-id="29acc-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="29acc-109">Comment : transformer la forme d’une arborescence XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-109">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="29acc-110">Montre comment transformer la forme d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="29acc-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="29acc-111">Comment : contrôler le Type d’une Projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-111">How to: Control the Type of a Projection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="29acc-112">Montre comment contrôler le type d'une requête [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="29acc-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="29acc-113">Procédure : projeter un nouveau Type (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-113">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="29acc-114">Montre comment projeter une collection d'un type défini par l'utilisateur à partir d'une requête [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="29acc-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="29acc-115">Procédure : projeter un graphique d’objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-115">How to: Project an Object Graph (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="29acc-116">Montre comment projeter un graphique d'objet plus complexe à partir d'une requête [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="29acc-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="29acc-117">Procédure : projeter un Type anonyme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-117">How to: Project an Anonymous Type (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="29acc-118">Montre comment projeter une collection d'objets anonymes à partir d'une requête [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="29acc-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="29acc-119">Comment : générer des fichiers texte à partir de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-119">How to: Generate Text Files from XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="29acc-120">Montre comment transformer un fichier XML en un fichier texte non XML.</span><span class="sxs-lookup"><span data-stu-id="29acc-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="29acc-121">Comment : générer du code XML à partir de fichiers CSV (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-121">How to: Generate XML from CSV Files (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="29acc-122">Montre comment utiliser [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour analyser un fichier CSV et générer du code XML à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="29acc-122">Shows how to use [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29acc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29acc-123">See Also</span></span>  
 [<span data-ttu-id="29acc-124">Interrogation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29acc-124">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
