---
title: "Techniques de requêtes (LINQ to XML) avancées (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79be877c-fadc-4dfb-9f03-426082b13656
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21a12ba1929b0e8fd24ae9e12404691222e397cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-query-techniques-linq-to-xml-visual-basic"></a><span data-ttu-id="8b5ac-102">Techniques de requêtes (LINQ to XML) avancées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-102">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8b5ac-103">Cette section fournit des exemples de techniques de requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] plus avancées.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b5ac-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8b5ac-104">In This Section</span></span>  
  
|<span data-ttu-id="8b5ac-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="8b5ac-105">Topic</span></span>|<span data-ttu-id="8b5ac-106">Description</span><span class="sxs-lookup"><span data-stu-id="8b5ac-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8b5ac-107">Comment : joindre deux Collections (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-107">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="8b5ac-108">Montre comment utiliser la clause `Join` pour tirer parti des relations dans des données XML.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="8b5ac-109">Comment : créer la hiérarchie à l’aide de regroupement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-109">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="8b5ac-110">Montre comment grouper des données, puis générer du code XML basé sur le regroupement.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="8b5ac-111">Comment : interroger LINQ to XML à l’aide de XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-111">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="8b5ac-112">Montre comment récupérer des collections basées sur des requêtes XPath.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="8b5ac-113">Comment : écrire un LINQ vers la méthode d’axe XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-113">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="8b5ac-114">Montre comment écrire une méthode d'axe [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b5ac-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="8b5ac-115">Comment : répertorier tous les nœuds dans une arborescence (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-115">How to: List All Nodes in a Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="8b5ac-116">Présente une méthode utilitaire qui répertorie tous les nœuds d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-116">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="8b5ac-117">Cela est utile pour le débogage de code qui modifie une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-117">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="8b5ac-118">Comment : récupérer des paragraphes à partir d’un Document Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-118">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="8b5ac-119">Présente du code qui ouvre un document Office Open XML, récupère les paragraphes dans une collection d’objets XElement, le texte des paragraphes et le style des paragraphes.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-119">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="8b5ac-120">Comment : modifier un Document Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-120">How to: Modify an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="8b5ac-121">Présente du code qui ouvre, modifie et enregistre un document Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-121">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="8b5ac-122">Comment : remplir une arborescence XML à partir du système de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-122">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="8b5ac-123">Présente du code qui crée une arborescence XML à partir du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="8b5ac-123">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b5ac-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b5ac-124">See Also</span></span>  
 [<span data-ttu-id="8b5ac-125">Interrogation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5ac-125">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
