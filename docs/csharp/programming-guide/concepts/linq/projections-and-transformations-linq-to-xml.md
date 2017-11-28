---
title: Projections et transformations (LINQ to XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb0457ab-1823-47e6-9d2d-c93c958cc913
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81172ebb440bc2737bbe3f1de0f1dd3cf6e086c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="projections-and-transformations-linq-to-xml-c"></a><span data-ttu-id="9fa2b-102">Projections et transformations (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-102">Projections and Transformations (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9fa2b-103">Cette section fournit des exemples de projections et de transformations [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa2b-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9fa2b-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9fa2b-104">In This Section</span></span>  
  
|<span data-ttu-id="9fa2b-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="9fa2b-105">Topic</span></span>|<span data-ttu-id="9fa2b-106">Description</span><span class="sxs-lookup"><span data-stu-id="9fa2b-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9fa2b-107">Guide pratique pour utiliser des dictionnaires à l’aide de LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-107">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="9fa2b-108">Montre comment transformer des dictionnaires au format XML et comment transformer du code XML en dictionnaires.</span><span class="sxs-lookup"><span data-stu-id="9fa2b-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="9fa2b-109">Guide pratique pour transformer la forme d’une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-109">How to: Transform the Shape of an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="9fa2b-110">Montre comment transformer la forme d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="9fa2b-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="9fa2b-111">Guide pratique pour contrôler le type d’une projection (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-111">How to: Control the Type of a Projection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="9fa2b-112">Montre comment contrôler le type d'une requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa2b-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="9fa2b-113">Guide pratique pour projeter un nouveau type (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-113">How to: Project a New Type (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="9fa2b-114">Montre comment projeter une collection d'un type défini par l'utilisateur à partir d'une requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa2b-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="9fa2b-115">Guide pratique pour projeter un graphique d’objet (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-115">How to: Project an Object Graph (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="9fa2b-116">Montre comment projeter un graphique d'objet plus complexe à partir d'une requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa2b-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="9fa2b-117">Guide pratique pour projeter un type anonyme (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-117">How to: Project an Anonymous Type (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="9fa2b-118">Montre comment projeter une collection d'objets anonymes à partir d'une requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fa2b-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="9fa2b-119">Guide pratique pour générer des fichiers texte à partir de données XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-119">How to: Generate Text Files from XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="9fa2b-120">Montre comment transformer un fichier XML en un fichier texte non XML.</span><span class="sxs-lookup"><span data-stu-id="9fa2b-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="9fa2b-121">Guide pratique pour générer du code XML à partir de fichiers CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-121">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="9fa2b-122">Montre comment utiliser [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pour analyser un fichier CSV et générer du code XML à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9fa2b-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fa2b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fa2b-123">See Also</span></span>  
 [<span data-ttu-id="9fa2b-124">Interrogation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9fa2b-124">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
