---
title: "Sérialisation d’arborescences XML (C#)"
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
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
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
ms.openlocfilehash: f3b8ee68065a056cccbf02d96bf5f21e7ccea16b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="e5aae-102">Sérialisation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e5aae-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="e5aae-103">Sérialiser une arborescence XML signifie générer du code XML à partir de l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="e5aae-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="e5aae-104">Vous pouvez sérialiser vers un fichier, vers une implémentation concrète de la classe <xref:System.IO.TextWriter> ou vers une implémentation concrète d'un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="e5aae-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="e5aae-105">Vous pouvez contrôler divers aspects de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e5aae-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="e5aae-106">Par exemple, vous pouvez contrôler s'il faut mettre en retrait le code XML sérialisé et s'il faut écrire une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="e5aae-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5aae-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e5aae-107">In This Section</span></span>  
  
|<span data-ttu-id="e5aae-108">Rubrique</span><span class="sxs-lookup"><span data-stu-id="e5aae-108">Topic</span></span>|<span data-ttu-id="e5aae-109">Description</span><span class="sxs-lookup"><span data-stu-id="e5aae-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e5aae-110">Conservation des espaces blancs lors de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="e5aae-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="e5aae-111">Décrit comment contrôler le comportement d’espace blanc lors de la sérialisation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="e5aae-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="e5aae-112">Sérialisation avec une déclaration XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e5aae-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="e5aae-113">Décrit comment sérialiser une arborescence XML qui inclut une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="e5aae-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="e5aae-114">Sérialisation vers des fichiers, TextWriters et XmlWriters</span><span class="sxs-lookup"><span data-stu-id="e5aae-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="e5aae-115">Décrit comment sérialiser un document vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="e5aae-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="e5aae-116">Sérialisation vers un XmlReader (appel de XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5aae-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="e5aae-117">Décrit comment créer un objet <xref:System.Xml.XmlReader> qui permet à un autre module de lire le contenu d'une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="e5aae-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5aae-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5aae-118">See Also</span></span>  
 [<span data-ttu-id="e5aae-119">Guide de programmation (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5aae-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

