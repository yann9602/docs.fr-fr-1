---
title: "Création d’arborescences XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: e86ba12b-17de-4579-81bb-66322b84cfbe
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c60746a3da6255e4c245febf55151b41186a75b7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="creating-xml-trees-visual-basic"></a><span data-ttu-id="5b5b6-102">Création d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b5b6-102">Creating XML Trees (Visual Basic)</span></span>
<span data-ttu-id="5b5b6-103">L'une des tâches XML les plus courantes consiste à construire une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="5b5b6-104">Cette section décrit plusieurs manières de procéder.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b5b6-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5b5b6-105">In This Section</span></span>  
  
|<span data-ttu-id="5b5b6-106">Rubrique</span><span class="sxs-lookup"><span data-stu-id="5b5b6-106">Topic</span></span>|<span data-ttu-id="5b5b6-107">Description</span><span class="sxs-lookup"><span data-stu-id="5b5b6-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5b5b6-108">Construction fonctionnelle (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b5b6-108">Functional Construction (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="5b5b6-109">Fournit une vue d'ensemble de la construction fonctionnelle dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b5b6-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span> <span data-ttu-id="5b5b6-110">La construction fonctionnelle vous permet de créer tout ou partie de votre arborescence XML en une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="5b5b6-111">Cette rubrique montre également comment incorporer des requêtes lors de la construction d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="5b5b6-112">Introduction aux littéraux XML en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b5b6-112">Introduction to XML Literals in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md)|<span data-ttu-id="5b5b6-113">Fournit une introduction rapide à la création d’arborescences dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] à l’aide de littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-113">Provides a quick introduction to creating trees in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] by using XML literals.</span></span> <span data-ttu-id="5b5b6-114">Cette rubrique inclut des liens vers la documentation [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] relative aux littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-114">This topic includes links to the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] documentation of XML literals.</span></span>|  
|[<span data-ttu-id="5b5b6-115">Clonage et Attachement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b5b6-115">Cloning vs. Attaching (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="5b5b6-116">Illustre la différence entre l’ajout de nœuds à partir d’une arborescence XML existante (nœuds clonés puis ajoutés) et l’ajout de nœuds sans parent (nœuds simplement attachés).</span><span class="sxs-lookup"><span data-stu-id="5b5b6-116">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="5b5b6-117">L’analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b5b6-117">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="5b5b6-118">Montre comment analyser du code XML provenant de diverses sources.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-118">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="5b5b6-119">se situe au-dessus de <xref:System.Xml.XmlReader>, qui est utilisé pour analyser le XML.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="5b5b6-119"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="5b5b6-120">Comment : remplir une arborescence XML avec un XmlWriter (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b5b6-120">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="5b5b6-121">Montre comment remplir une arborescence XML à l’aide d’un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="5b5b6-121">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="5b5b6-122">Comment : valider à l’aide de XSD (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b5b6-122">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="5b5b6-123">Montre comment valider une arborescence XML à l’aide de XSD.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-123">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="5b5b6-124">Contenu valide des objets XElement et XDocument</span><span class="sxs-lookup"><span data-stu-id="5b5b6-124">Valid Content of XElement and XDocument Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects.md)|<span data-ttu-id="5b5b6-125">Décrit les arguments valides qui peuvent être passés aux constructeurs et méthodes utilisés pour ajouter du contenu aux éléments et aux documents.</span><span class="sxs-lookup"><span data-stu-id="5b5b6-125">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b5b6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b5b6-126">See Also</span></span>  
 [<span data-ttu-id="5b5b6-127">Guide de programmation (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b5b6-127">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
