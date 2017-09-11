---
title: Conservation des espaces lors Serializing2 | Documents Microsoft
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
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
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
ms.openlocfilehash: de06e1a5a217644a2eae99f8c7752ee780594d22
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="087a4-102">Conservation des espaces blancs lors de la sérialisation</span><span class="sxs-lookup"><span data-stu-id="087a4-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="087a4-103">Cette rubrique décrit comment contrôler les espaces blancs lors de la sérialisation d'une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="087a4-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="087a4-104">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="087a4-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="087a4-105">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="087a4-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="087a4-106">Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="087a4-106">This is the default behavior for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="087a4-107">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="087a4-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="087a4-108">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="087a4-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="087a4-109">Pour ce faire dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous devez conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="087a4-109">To do this in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="087a4-110">Comportement d'espace blanc des méthodes qui sérialisent des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="087a4-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="087a4-111">Les méthodes suivantes dans le <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XDocument>classes sérialisent une arborescence XML.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="087a4-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="087a4-112">Vous pouvez sérialiser une arborescence XML dans un fichier, un <xref:System.IO.TextReader>, ou un <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> </xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="087a4-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="087a4-113">La méthode `ToString` sérialise vers une chaîne.</span><span class="sxs-lookup"><span data-stu-id="087a4-113">The `ToString` method serializes to a string.</span></span>  
  
-   <span data-ttu-id="087a4-114"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="087a4-114"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="087a4-115"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="087a4-115"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="087a4-116"><xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="087a4-116"><xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="087a4-117"><xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="087a4-117"><xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="087a4-118">Si la méthode ne prend pas <xref:System.Xml.Linq.SaveOptions>en tant qu’argument, la méthode formatera (en retrait) le code XML sérialisé.</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="087a4-118">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="087a4-119">Dans ce cas, tous les espaces blancs non significatifs dans l'arborescence XML seront ignorés.</span><span class="sxs-lookup"><span data-stu-id="087a4-119">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="087a4-120">Si la méthode prend <xref:System.Xml.Linq.SaveOptions>en tant qu’argument, vous pouvez spécifier que la méthode pas mettre en forme (en retrait) le code XML sérialisé.</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="087a4-120">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="087a4-121">Dans ce cas, tous les espaces blancs dans l’arborescence XML seront conservés.</span><span class="sxs-lookup"><span data-stu-id="087a4-121">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="087a4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="087a4-122">See Also</span></span>  
 [<span data-ttu-id="087a4-123">Sérialisation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="087a4-123">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
