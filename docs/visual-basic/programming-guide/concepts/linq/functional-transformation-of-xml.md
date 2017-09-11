---
title: Transformation fonctionnelle XML (Visual Basic) | Documents Microsoft
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
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8c41d464d5b214520ca5e36877fb59d45c851786
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="functional-transformation-of-xml-visual-basic"></a><span data-ttu-id="a0629-102">Transformation fonctionnelle XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0629-102">Functional Transformation of XML (Visual Basic)</span></span>
<span data-ttu-id="a0629-103">Cette rubrique traite de l'approche de transformation fonctionnelle pure permettant de modifier des documents XML et l'oppose à une approche procédurale.</span><span class="sxs-lookup"><span data-stu-id="a0629-103">This topic discusses the pure functional transformation approach to modifying XML documents, and contrasts it with a procedural approach.</span></span>  
  
## <a name="modifying-an-xml-document"></a><span data-ttu-id="a0629-104">Modification d'un document XML</span><span class="sxs-lookup"><span data-stu-id="a0629-104">Modifying an XML Document</span></span>  
 <span data-ttu-id="a0629-105">L'une des tâches les plus courantes pour un programmeur XML consiste à transformer du code XML d'une forme en une autre.</span><span class="sxs-lookup"><span data-stu-id="a0629-105">One of the most common tasks for an XML programmer is transforming XML from one shape to another.</span></span> <span data-ttu-id="a0629-106">La forme d'un document XML est la structure du document, qui inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a0629-106">The shape of an XML document is the structure of the document, which includes the following:</span></span>  
  
-   <span data-ttu-id="a0629-107">la hiérarchie exprimée par le document ;</span><span class="sxs-lookup"><span data-stu-id="a0629-107">The hierarchy expressed by the document.</span></span>  
  
-   <span data-ttu-id="a0629-108">les noms des éléments et des attributs ;</span><span class="sxs-lookup"><span data-stu-id="a0629-108">The element and attribute names.</span></span>  
  
-   <span data-ttu-id="a0629-109">les types de données des éléments et attributs.</span><span class="sxs-lookup"><span data-stu-id="a0629-109">The data types of the elements and attributes.</span></span>  
  
 <span data-ttu-id="a0629-110">En général, l'approche la plus efficace pour transformer du code XML d'une forme en une autre consiste à utiliser la transformation fonctionnelle pure.</span><span class="sxs-lookup"><span data-stu-id="a0629-110">In general, the most effective approach to transforming XML from one shape to another is that of pure functional transformation.</span></span> <span data-ttu-id="a0629-111">Avec cette approche, la principale tâche du programmeur est de créer une transformation qui est appliquée à l'ensemble du document XML (ou à un ou plusieurs nœuds strictement définis).</span><span class="sxs-lookup"><span data-stu-id="a0629-111">In this approach, the primary programmer task is to create a transformation which is applied to the entire XML document (or to one or more strictly defined nodes).</span></span> <span data-ttu-id="a0629-112">La transformation fonctionnelle offre sans aucun doute la plus grande facilité de codage (une fois que le programmeur s'est familiarisé avec cette approche) et la plus grande facilité de maintenance du code, et elle est souvent plus compacte que les autres approches.</span><span class="sxs-lookup"><span data-stu-id="a0629-112">Functional transformation is arguably the easiest to code (after a programmer is familiar with the approach), yields the most maintainable code, and is often more compact than alternative approaches.</span></span>  
  
### <a name="xml-functional-transformational-technologies"></a><span data-ttu-id="a0629-113">Technologies de transformation fonctionnelle XML</span><span class="sxs-lookup"><span data-stu-id="a0629-113">XML Functional Transformational Technologies</span></span>  
 <span data-ttu-id="a0629-114">Microsoft propose deux technologies de transformation fonctionnelle pour une utilisation sur des documents XML : XSLT et LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="a0629-114">Microsoft offers two functional transformation technologies for use on XML documents: XSLT and LINQ to XML.</span></span> <span data-ttu-id="a0629-115">XSLT est pris en charge dans les <xref:System.Xml.Xsl>espace de noms managé dans l’implémentation COM native de MSXML.</xref:System.Xml.Xsl></span><span class="sxs-lookup"><span data-stu-id="a0629-115">XSLT is supported in the <xref:System.Xml.Xsl> managed namespace and in the native COM implementation of MSXML.</span></span> <span data-ttu-id="a0629-116">Bien que XSLT soit une technologie robuste pour la manipulation de documents XML, elle requiert un savoir-faire dans un domaine spécialisé, à savoir le langage XSLT et ses API de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="a0629-116">Although XSLT is a robust technology for manipulating XML documents, it requires expertise in a specialized domain, namely the XSLT language and its supporting APIs.</span></span>  
  
 <span data-ttu-id="a0629-117">LINQ to XML procure les outils nécessaires pour coder des transformations fonctionnelles pures de manière expressive et puissante, dans du code C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a0629-117">LINQ to XML provides the tools necessary to code pure functional transformations in an expressive and powerful way, within C# or Visual Basic code.</span></span> <span data-ttu-id="a0629-118">Par exemple, bon nombre des exemples dans la documentation LINQ to XML utilisent une approche fonctionnelle pure.</span><span class="sxs-lookup"><span data-stu-id="a0629-118">For example, many of the examples in the LINQ to XML documentation use a pure functional approach.</span></span> <span data-ttu-id="a0629-119">En outre, dans le [didacticiel : manipulation de contenu dans un WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) (didacticiel), nous permet de LINQ to XML dans une approche fonctionnelle manipulent des informations dans un document Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="a0629-119">Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.</span></span>  
  
 <span data-ttu-id="a0629-120">Pour une comparaison plus complète de LINQ to XML avec d’autres technologies XML Microsoft, consultez [LINQ to XML vs. Autres Technologies XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).</span><span class="sxs-lookup"><span data-stu-id="a0629-120">For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. Other XML Technologies](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).</span></span>  
  
 <span data-ttu-id="a0629-121">XSLT est l'outil recommandé pour les transformations centrées sur les documents lorsque le document source a une structure irrégulière.</span><span class="sxs-lookup"><span data-stu-id="a0629-121">XSLT is the recommended tool for  document-centric transformations when the source document has an irregular structure.</span></span> <span data-ttu-id="a0629-122">Toutefois, LINQ to XML peut également effectuer des transformations centrées sur les documents.</span><span class="sxs-lookup"><span data-stu-id="a0629-122">However, LINQ to XML can also perform document-centric transforms.</span></span> <span data-ttu-id="a0629-123">Pour plus d’informations, consultez [Comment : utiliser des Annotations pour transformer des arborescences LINQ to XML en un Style XSLT (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).</span><span class="sxs-lookup"><span data-stu-id="a0629-123">For more information, see [How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0629-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0629-124">See Also</span></span>  
 <span data-ttu-id="a0629-125">[Introduction aux Transformations fonctionnelles pures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="a0629-125">[Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
<span data-ttu-id="a0629-126"> [LINQ to XML, différences par rapport à Autres Technologies XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md) </span><span class="sxs-lookup"><span data-stu-id="a0629-126"> [LINQ to XML vs. Other XML Technologies](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md) </span></span>  
<span data-ttu-id="a0629-127"> [LINQ to XML, différences par rapport à d’autres technologies XML](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)</span><span class="sxs-lookup"><span data-stu-id="a0629-127"> [LINQ to XML vs. Other XML Technologies](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)</span></span>
