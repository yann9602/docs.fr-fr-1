---
title: "Techniques de requêtes (LINQ to XML) avancées (Visual Basic) | Documents Microsoft"
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
ms.assetid: 79be877c-fadc-4dfb-9f03-426082b13656
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6983fa5b9637210bb3c56e8f693eb4f956dab0a8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="advanced-query-techniques-linq-to-xml-visual-basic"></a><span data-ttu-id="ace55-102">Techniques de requêtes (LINQ to XML) avancées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-102">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ace55-103">Cette section fournit des exemples de techniques de requêtes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] plus avancées.</span><span class="sxs-lookup"><span data-stu-id="ace55-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ace55-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ace55-104">In This Section</span></span>  
  
|<span data-ttu-id="ace55-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="ace55-105">Topic</span></span>|<span data-ttu-id="ace55-106">Description</span><span class="sxs-lookup"><span data-stu-id="ace55-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ace55-107">Comment : joindre deux Collections (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-107">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="ace55-108">Montre comment utiliser la clause `Join` pour tirer parti des relations dans des données XML.</span><span class="sxs-lookup"><span data-stu-id="ace55-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="ace55-109">Comment : créer la hiérarchie à l’aide de regroupement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-109">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="ace55-110">Montre comment grouper des données, puis générer du code XML basé sur le regroupement.</span><span class="sxs-lookup"><span data-stu-id="ace55-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="ace55-111">Comment : interroger LINQ to XML à l’aide de XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-111">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="ace55-112">Montre comment récupérer des collections basées sur des requêtes XPath.</span><span class="sxs-lookup"><span data-stu-id="ace55-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="ace55-113">Comment : écrire un LINQ vers la méthode d’axe XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-113">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="ace55-114">Montre comment écrire une méthode d'axe [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="ace55-114">Shows how to write a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axis method.</span></span>|  
|[<span data-ttu-id="ace55-115">Comment : répertorier tous les nœuds dans une arborescence (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-115">How to: List All Nodes in a Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="ace55-116">Présente une méthode utilitaire qui répertorie tous les nœuds d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="ace55-116">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="ace55-117">Cela est utile pour le débogage de code qui modifie une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="ace55-117">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="ace55-118">Comment : récupérer des paragraphes à partir d’un Document Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-118">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="ace55-119">Présente du code qui ouvre un document Office Open XML, récupère les paragraphes dans une collection d’objets XElement, le texte des paragraphes et le style des paragraphes.</span><span class="sxs-lookup"><span data-stu-id="ace55-119">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="ace55-120">Comment : modifier un Document Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-120">How to: Modify an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="ace55-121">Présente du code qui ouvre, modifie et enregistre un document Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="ace55-121">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="ace55-122">Comment : remplir une arborescence XML à partir du système de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-122">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="ace55-123">Présente du code qui crée une arborescence XML à partir du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ace55-123">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ace55-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ace55-124">See Also</span></span>  
 [<span data-ttu-id="ace55-125">Interrogation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace55-125">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
