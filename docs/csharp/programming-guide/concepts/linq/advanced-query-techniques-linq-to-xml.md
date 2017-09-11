---
title: "Techniques de requêtes avancées (LINQ to XML) (C#)"
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
ms.assetid: 028d978e-215b-4d50-ba70-adce0659386d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 91460ed99854edda829503d451728c4274d7ba2b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="advanced-query-techniques-linq-to-xml-c"></a><span data-ttu-id="5a39b-102">Techniques de requêtes avancées (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-102">Advanced Query Techniques (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5a39b-103">Cette section fournit des exemples de techniques de requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] plus avancées.</span><span class="sxs-lookup"><span data-stu-id="5a39b-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a39b-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5a39b-104">In This Section</span></span>  
  
|<span data-ttu-id="5a39b-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="5a39b-105">Topic</span></span>|<span data-ttu-id="5a39b-106">Description</span><span class="sxs-lookup"><span data-stu-id="5a39b-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5a39b-107">Guide pratique pour joindre deux collections (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-107">How to: Join Two Collections (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="5a39b-108">Montre comment utiliser la clause `Join` pour tirer parti des relations dans des données XML.</span><span class="sxs-lookup"><span data-stu-id="5a39b-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="5a39b-109">Guide pratique pour créer une hiérarchie à l’aide de regroupements (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-109">How to: Create Hierarchy Using Grouping (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="5a39b-110">Montre comment grouper des données, puis générer du code XML basé sur le regroupement.</span><span class="sxs-lookup"><span data-stu-id="5a39b-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="5a39b-111">Guide pratique pour interroger LINQ to XML à l’aide de XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-111">How to: Query LINQ to XML Using XPath (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="5a39b-112">Montre comment récupérer des collections basées sur des requêtes XPath.</span><span class="sxs-lookup"><span data-stu-id="5a39b-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="5a39b-113">Guide pratique pour écrire une méthode d’axe LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-113">How to: Write a LINQ to XML Axis Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="5a39b-114">Montre comment écrire une méthode d'axe [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a39b-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="5a39b-115">Guide pratique pour effectuer des transformations de streaming au format XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-115">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transformations-of-text-to-xml.md)|<span data-ttu-id="5a39b-116">Montre comment transformer des fichiers texte de très grande taille au format XML tout en maintenant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="5a39b-116">Shows how to transform very large text files into XML while maintaining a small memory footprint.</span></span>|  
|[<span data-ttu-id="5a39b-117">Guide pratique pour répertorier tous les nœuds dans une arborescence (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-117">How to: List All Nodes in a Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="5a39b-118">Présente une méthode utilitaire qui répertorie tous les nœuds d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="5a39b-118">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="5a39b-119">Cela est utile pour le débogage de code qui modifie une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="5a39b-119">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="5a39b-120">Guide pratique pour récupérer des paragraphes à partir d’un document Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-120">How to: Retrieve Paragraphs from an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="5a39b-121">Présente du code qui ouvre un document Office Open XML, récupère les paragraphes dans une collection d’objets XElement, le texte des paragraphes et le style des paragraphes.</span><span class="sxs-lookup"><span data-stu-id="5a39b-121">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="5a39b-122">Guide pratique pour modifier un document Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-122">How to: Modify an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="5a39b-123">Présente du code qui ouvre, modifie et enregistre un document Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="5a39b-123">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="5a39b-124">Guide pratique pour remplir une arborescence XML à partir du système de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-124">How to: Populate an XML Tree from the File System (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="5a39b-125">Présente du code qui crée une arborescence XML à partir du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="5a39b-125">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a39b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a39b-126">See Also</span></span>  
 [<span data-ttu-id="5a39b-127">Interrogation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5a39b-127">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)

