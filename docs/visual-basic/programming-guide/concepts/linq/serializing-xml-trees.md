---
title: "Sérialisation d’arborescences XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
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
ms.openlocfilehash: a63e875b1c1391ec1bb2b0ae64be9f9cff28d87d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="2ec10-102">Sérialisation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec10-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="2ec10-103">Sérialiser une arborescence XML signifie générer du code XML à partir de l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="2ec10-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="2ec10-104">Vous pouvez sérialiser vers un fichier, vers une implémentation concrète de la <xref:System.IO.TextWriter>(classe), ou vers une implémentation concrète d’un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter></span><span class="sxs-lookup"><span data-stu-id="2ec10-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="2ec10-105">Vous pouvez contrôler divers aspects de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="2ec10-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="2ec10-106">Par exemple, vous pouvez contrôler s'il faut mettre en retrait le code XML sérialisé et s'il faut écrire une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="2ec10-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ec10-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2ec10-107">In This Section</span></span>  
  
|<span data-ttu-id="2ec10-108">Rubrique</span><span class="sxs-lookup"><span data-stu-id="2ec10-108">Topic</span></span>|<span data-ttu-id="2ec10-109">Description</span><span class="sxs-lookup"><span data-stu-id="2ec10-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2ec10-110">Conservation des espaces blancs lors de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="2ec10-110">Preserving White Space While Serializing</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="2ec10-111">Décrit comment contrôler le comportement d’espace blanc lors de la sérialisation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="2ec10-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="2ec10-112">Sérialisation avec une déclaration XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec10-112">Serializing with an XML Declaration (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="2ec10-113">Décrit comment sérialiser une arborescence XML qui inclut une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="2ec10-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="2ec10-114">Sérialisation vers des fichiers, TextWriters et XmlWriters</span><span class="sxs-lookup"><span data-stu-id="2ec10-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="2ec10-115">Décrit comment sérialiser un document vers un <xref:System.IO.File>, un <xref:System.IO.TextWriter>, ou un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="2ec10-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="2ec10-116">Sérialisation vers un XmlReader (appel de XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec10-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="2ec10-117">Décrit comment créer un <xref:System.Xml.XmlReader>qui permet à un autre module de lire le contenu d’une arborescence XML.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="2ec10-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ec10-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ec10-118">See Also</span></span>  
 [<span data-ttu-id="2ec10-119">Guide de programmation (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec10-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
