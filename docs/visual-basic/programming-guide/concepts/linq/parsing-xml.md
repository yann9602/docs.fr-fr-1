---
title: "L’analyse XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: af4ecce89f2f45069a48ce62826509f795dcf211
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="215e2-102">L’analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="215e2-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="215e2-103">Les rubriques de cette section décrivent comment analyser des documents XML.</span><span class="sxs-lookup"><span data-stu-id="215e2-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="215e2-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="215e2-104">In This Section</span></span>  
  
|<span data-ttu-id="215e2-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="215e2-105">Topic</span></span>|<span data-ttu-id="215e2-106">Description</span><span class="sxs-lookup"><span data-stu-id="215e2-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="215e2-107">Comment : analyser une chaîne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="215e2-107">How to: Parse a String (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="215e2-108">Montre comment analyser une chaîne pour créer une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="215e2-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="215e2-109">Comment : charger du code XML à partir d’un fichier (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="215e2-109">How to: Load XML from a File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="215e2-110">Montre comment charger du code XML à partir d’un URI en utilisant la <xref:System.Xml.Linq.XElement.Load%2A>méthode.</xref:System.Xml.Linq.XElement.Load%2A></span><span class="sxs-lookup"><span data-stu-id="215e2-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="215e2-111">Conservation des espaces lors du chargement ou de l'analyse de code XML</span><span class="sxs-lookup"><span data-stu-id="215e2-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="215e2-112">Décrit comment contrôler le comportement d'espace blanc de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] lors du chargement d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="215e2-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="215e2-113">Comment : intercepter des erreurs (Visual Basic) d’analyse</span><span class="sxs-lookup"><span data-stu-id="215e2-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="215e2-114">Montre comment détecter du code XML incorrect ou non valide.</span><span class="sxs-lookup"><span data-stu-id="215e2-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="215e2-115">Comment : créer une arborescence à partir d’un XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="215e2-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="215e2-116">Montre comment créer une arborescence XML directement à partir d’un <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="215e2-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="215e2-117">Procédure : diffuser des fragments XML en continu à partir d’un XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="215e2-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="215e2-118">Montre comment diffuser des fragments XML à l’aide d’un <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="215e2-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="215e2-119">Lorsque vous devez traiter des fichiers XML arbitrairement grands, il peut être impossible de charger l'intégralité de l'arborescence XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="215e2-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="215e2-120">Au lieu de cela, vous pouvez diffuser des fragments XML en continu.</span><span class="sxs-lookup"><span data-stu-id="215e2-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="215e2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="215e2-121">See Also</span></span>  
 [<span data-ttu-id="215e2-122">Création d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="215e2-122">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
