---
title: "Conservation des espaces lors du chargement ou de l’analyse XML2 | Documents Microsoft"
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
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
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
ms.openlocfilehash: a2872c1e2354c0a0bd106f7fb945542ce37e7774
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="3455c-102">Conservation des espaces lors du chargement ou de l'analyse de code XML</span><span class="sxs-lookup"><span data-stu-id="3455c-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="3455c-103">Cette rubrique décrit comment contrôler le comportement d'espace blanc de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="3455c-103">This topic describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="3455c-104">Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="3455c-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="3455c-105">Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés.</span><span class="sxs-lookup"><span data-stu-id="3455c-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="3455c-106">Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="3455c-106">This is the default behavior for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="3455c-107">Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="3455c-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="3455c-108">Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière.</span><span class="sxs-lookup"><span data-stu-id="3455c-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="3455c-109">Pour ce faire dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous devez conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.</span><span class="sxs-lookup"><span data-stu-id="3455c-109">To do this in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="3455c-110">Cette rubrique décrit le comportement des espaces blancs des méthodes qui remplissent les arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="3455c-110">This topic describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="3455c-111">Pour plus d’informations sur le contrôle des espaces blancs lorsque vous sérialisez des arborescences XML, consultez [conserver un espace blanc tandis que sérialisation](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="3455c-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="3455c-112">Comportement des méthodes qui remplissent des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="3455c-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="3455c-113">Les méthodes suivantes dans le <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XDocument>classes de remplissent une arborescence XML.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="3455c-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="3455c-114">Vous pouvez remplir une arborescence XML à partir d’un fichier, un <xref:System.IO.TextReader>, un <xref:System.Xml.XmlReader>, ou une chaîne :</xref:System.Xml.XmlReader> </xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="3455c-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <span data-ttu-id="3455c-115"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3455c-115"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="3455c-116"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3455c-116"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="3455c-117"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3455c-117"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="3455c-118"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3455c-118"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="3455c-119">Si la méthode ne prend pas <xref:System.Xml.Linq.LoadOptions>en tant qu’argument, la méthode ne conserve pas les espaces blancs non significatifs.</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="3455c-119">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="3455c-120">Dans la plupart des cas, si la méthode accepte <xref:System.Xml.Linq.LoadOptions>en tant qu’argument, vous pouvez éventuellement conserver les espaces blancs non significatifs en tant que nœuds de texte dans l’arborescence XML.</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="3455c-120">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="3455c-121">Toutefois, si la méthode charge les données XML un <xref:System.Xml.XmlReader>, le <xref:System.Xml.XmlReader>détermine si les espaces blancs sont conservés.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="3455c-121">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="3455c-122">Définition <xref:System.Xml.Linq.LoadOptions>n’a aucun effet.</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="3455c-122">Setting <xref:System.Xml.Linq.LoadOptions> will have no effect.</span></span>  
  
 <span data-ttu-id="3455c-123">Avec ces méthodes, si les espaces blancs sont conservés, espaces blancs non significatifs sont insérés dans l’arborescence XML en tant que <xref:System.Xml.Linq.XText>nœuds.</xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="3455c-123">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="3455c-124">Si les espaces ne sont pas conservés, aucun nœud de texte n'est inséré.</span><span class="sxs-lookup"><span data-stu-id="3455c-124">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="3455c-125">Vous pouvez créer une arborescence XML à l’aide d’un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="3455c-125">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="3455c-126">Les nœuds qui sont écrits dans le <xref:System.Xml.XmlWriter>sont remplis dans l’arborescence.</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="3455c-126">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="3455c-127">Toutefois, lorsque vous générez une arborescence XML à l’aide de cette méthode, tous les nœuds sont conservés, qu’ils soient constitués d’espaces ou non et que ces espaces soient significatifs ou non.</span><span class="sxs-lookup"><span data-stu-id="3455c-127">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3455c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3455c-128">See Also</span></span>  
 [<span data-ttu-id="3455c-129">L’analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3455c-129">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
