---
title: "Création d’arborescences XML (C#)"
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
ms.assetid: bccc3e0a-c08c-468e-9d30-e075670fdace
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 99b197b86096b803b9732ab2546b23ff59e3e2fe
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="creating-xml-trees-c"></a><span data-ttu-id="4be48-102">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4be48-102">Creating XML Trees (C#)</span></span>
<span data-ttu-id="4be48-103">L'une des tâches XML les plus courantes consiste à construire une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="4be48-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="4be48-104">Cette section décrit plusieurs manières de procéder.</span><span class="sxs-lookup"><span data-stu-id="4be48-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4be48-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4be48-105">In This Section</span></span>  
  
|<span data-ttu-id="4be48-106">Rubrique</span><span class="sxs-lookup"><span data-stu-id="4be48-106">Topic</span></span>|<span data-ttu-id="4be48-107">Description</span><span class="sxs-lookup"><span data-stu-id="4be48-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4be48-108">Construction fonctionnelle (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4be48-108">Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="4be48-109">Fournit une vue d'ensemble de la construction fonctionnelle dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4be48-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="4be48-110">La construction fonctionnelle vous permet de créer tout ou partie de votre arborescence XML en une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="4be48-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="4be48-111">Cette rubrique montre également comment incorporer des requêtes lors de la construction d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="4be48-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="4be48-112">Création d’arborescences XML en C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4be48-112">Creating XML Trees in C# (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md)|<span data-ttu-id="4be48-113">Montre comment créer des arborescences en C#.</span><span class="sxs-lookup"><span data-stu-id="4be48-113">Shows how to create trees in C#.</span></span>|  
|[<span data-ttu-id="4be48-114">Clonage et Attachement (C#)</span><span class="sxs-lookup"><span data-stu-id="4be48-114">Cloning vs. Attaching (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="4be48-115">Illustre la différence entre l’ajout de nœuds à partir d’une arborescence XML existante (nœuds clonés puis ajoutés) et l’ajout de nœuds sans parent (nœuds simplement attachés).</span><span class="sxs-lookup"><span data-stu-id="4be48-115">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="4be48-116">Analyse de code XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4be48-116">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="4be48-117">Montre comment analyser du code XML provenant de diverses sources.</span><span class="sxs-lookup"><span data-stu-id="4be48-117">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4be48-118"> se situe par-dessus <xref:System.Xml.XmlReader>, qui est utilisé pour analyser le code XML.</span><span class="sxs-lookup"><span data-stu-id="4be48-118"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="4be48-119">Guide pratique pour remplir une arborescence XML avec un XmlWriter (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4be48-119">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="4be48-120">Montre comment remplir une arborescence XML à l'aide d'un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4be48-120">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="4be48-121">Guide pratique pour valider à l’aide de XSD (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4be48-121">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="4be48-122">Montre comment valider une arborescence XML à l’aide de XSD.</span><span class="sxs-lookup"><span data-stu-id="4be48-122">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="4be48-123">Contenu valide des objets XElement et XDocument</span><span class="sxs-lookup"><span data-stu-id="4be48-123">Valid Content of XElement and XDocument Objects</span></span>](../../../../csharp/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects3.md)|<span data-ttu-id="4be48-124">Décrit les arguments valides qui peuvent être passés aux constructeurs et méthodes utilisés pour ajouter du contenu aux éléments et aux documents.</span><span class="sxs-lookup"><span data-stu-id="4be48-124">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4be48-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4be48-125">See Also</span></span>  
 [<span data-ttu-id="4be48-126">Guide de programmation (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4be48-126">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

