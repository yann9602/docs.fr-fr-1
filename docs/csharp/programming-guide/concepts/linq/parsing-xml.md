---
title: Analyse de code XML (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d262fd2177ac77ab5109362f94cc51d03c9563c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-xml-c"></a><span data-ttu-id="af737-102">Analyse de code XML (C#)</span><span class="sxs-lookup"><span data-stu-id="af737-102">Parsing XML (C#)</span></span>
<span data-ttu-id="af737-103">Les rubriques de cette section décrivent comment analyser des documents XML.</span><span class="sxs-lookup"><span data-stu-id="af737-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af737-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="af737-104">In This Section</span></span>  
  
|<span data-ttu-id="af737-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="af737-105">Topic</span></span>|<span data-ttu-id="af737-106">Description</span><span class="sxs-lookup"><span data-stu-id="af737-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="af737-107">Guide pratique pour analyser une chaîne (C#)</span><span class="sxs-lookup"><span data-stu-id="af737-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="af737-108">Montre comment analyser une chaîne pour créer une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="af737-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="af737-109">Guide pratique pour charger du code XML à partir d’un fichier (C#)</span><span class="sxs-lookup"><span data-stu-id="af737-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="af737-110">Montre comment charger du code XML à partir d'un URI en utilisant la méthode <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="af737-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="af737-111">Conservation des espaces lors du chargement ou de l'analyse de code XML</span><span class="sxs-lookup"><span data-stu-id="af737-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="af737-112">Décrit comment contrôler le comportement d'espace blanc de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lors du chargement d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="af737-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="af737-113">Guide pratique pour intercepter les erreurs d’analyse (C#)</span><span class="sxs-lookup"><span data-stu-id="af737-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="af737-114">Montre comment détecter du code XML incorrect ou non valide.</span><span class="sxs-lookup"><span data-stu-id="af737-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="af737-115">Guide pratique pour créer une arborescence à partir d’un XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="af737-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="af737-116">Montre comment créer une arborescence XML directement à partir d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="af737-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="af737-117">Guide pratique pour diffuser des fragments XML en continu à partir d’un XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="af737-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="af737-118">Montre comment diffuser des fragments XML en continu à l'aide d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="af737-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="af737-119">Lorsque vous devez traiter des fichiers XML arbitrairement grands, il peut être impossible de charger l'intégralité de l'arborescence XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="af737-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="af737-120">Au lieu de cela, vous pouvez diffuser des fragments XML en continu.</span><span class="sxs-lookup"><span data-stu-id="af737-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af737-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af737-121">See Also</span></span>  
 [<span data-ttu-id="af737-122">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="af737-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
