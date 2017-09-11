---
title: "Transformation fonctionnelle de données XML (C#)"
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
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 57b4d25b7c2257c16401339f590b3487fba7d12a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="functional-transformation-of-xml-c"></a><span data-ttu-id="3f212-102">Transformation fonctionnelle de données XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3f212-102">Functional Transformation of XML (C#)</span></span>
<span data-ttu-id="3f212-103">Cette rubrique traite de l'approche de transformation fonctionnelle pure permettant de modifier des documents XML et l'oppose à une approche procédurale.</span><span class="sxs-lookup"><span data-stu-id="3f212-103">This topic discusses the pure functional transformation approach to modifying XML documents, and contrasts it with a procedural approach.</span></span>  
  
## <a name="modifying-an-xml-document"></a><span data-ttu-id="3f212-104">Modification d'un document XML</span><span class="sxs-lookup"><span data-stu-id="3f212-104">Modifying an XML Document</span></span>  
 <span data-ttu-id="3f212-105">L'une des tâches les plus courantes pour un programmeur XML consiste à transformer du code XML d'une forme en une autre.</span><span class="sxs-lookup"><span data-stu-id="3f212-105">One of the most common tasks for an XML programmer is transforming XML from one shape to another.</span></span> <span data-ttu-id="3f212-106">La forme d'un document XML est la structure du document, qui inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3f212-106">The shape of an XML document is the structure of the document, which includes the following:</span></span>  
  
-   <span data-ttu-id="3f212-107">la hiérarchie exprimée par le document ;</span><span class="sxs-lookup"><span data-stu-id="3f212-107">The hierarchy expressed by the document.</span></span>  
  
-   <span data-ttu-id="3f212-108">les noms des éléments et des attributs ;</span><span class="sxs-lookup"><span data-stu-id="3f212-108">The element and attribute names.</span></span>  
  
-   <span data-ttu-id="3f212-109">les types de données des éléments et attributs.</span><span class="sxs-lookup"><span data-stu-id="3f212-109">The data types of the elements and attributes.</span></span>  
  
 <span data-ttu-id="3f212-110">En général, l'approche la plus efficace pour transformer du code XML d'une forme en une autre consiste à utiliser la transformation fonctionnelle pure.</span><span class="sxs-lookup"><span data-stu-id="3f212-110">In general, the most effective approach to transforming XML from one shape to another is that of pure functional transformation.</span></span> <span data-ttu-id="3f212-111">Avec cette approche, la principale tâche du programmeur est de créer une transformation qui est appliquée à l'ensemble du document XML (ou à un ou plusieurs nœuds strictement définis).</span><span class="sxs-lookup"><span data-stu-id="3f212-111">In this approach, the primary programmer task is to create a transformation which is applied to the entire XML document (or to one or more strictly defined nodes).</span></span> <span data-ttu-id="3f212-112">La transformation fonctionnelle offre sans aucun doute la plus grande facilité de codage (une fois que le programmeur s'est familiarisé avec cette approche) et la plus grande facilité de maintenance du code, et elle est souvent plus compacte que les autres approches.</span><span class="sxs-lookup"><span data-stu-id="3f212-112">Functional transformation is arguably the easiest to code (after a programmer is familiar with the approach), yields the most maintainable code, and is often more compact than alternative approaches.</span></span>  
  
### <a name="xml-functional-transformational-technologies"></a><span data-ttu-id="3f212-113">Technologies de transformation fonctionnelle XML</span><span class="sxs-lookup"><span data-stu-id="3f212-113">XML Functional Transformational Technologies</span></span>  
 <span data-ttu-id="3f212-114">Microsoft propose deux technologies de transformation fonctionnelle pour une utilisation sur des documents XML : XSLT et LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="3f212-114">Microsoft offers two functional transformation technologies for use on XML documents: XSLT and LINQ to XML.</span></span> <span data-ttu-id="3f212-115">XSLT est pris en charge dans l'espace de noms managé <xref:System.Xml.Xsl> et dans l'implémentation COM native de MSXML.</span><span class="sxs-lookup"><span data-stu-id="3f212-115">XSLT is supported in the <xref:System.Xml.Xsl> managed namespace and in the native COM implementation of MSXML.</span></span> <span data-ttu-id="3f212-116">Bien que XSLT soit une technologie robuste pour la manipulation de documents XML, elle requiert un savoir-faire dans un domaine spécialisé, à savoir le langage XSLT et ses API de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3f212-116">Although XSLT is a robust technology for manipulating XML documents, it requires expertise in a specialized domain, namely the XSLT language and its supporting APIs.</span></span>  
  
 <span data-ttu-id="3f212-117">LINQ to XML procure les outils nécessaires pour coder des transformations fonctionnelles pures de manière expressive et puissante, dans du code C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3f212-117">LINQ to XML provides the tools necessary to code pure functional transformations in an expressive and powerful way, within C# or Visual Basic code.</span></span> <span data-ttu-id="3f212-118">Par exemple, bon nombre des exemples dans la documentation LINQ to XML utilisent une approche fonctionnelle pure.</span><span class="sxs-lookup"><span data-stu-id="3f212-118">For example, many of the examples in the LINQ to XML documentation use a pure functional approach.</span></span> <span data-ttu-id="3f212-119">En outre, dans le [Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md), nous utilisons LINQ to XML dans une approche fonctionnelle afin de manipuler des informations dans un document Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="3f212-119">Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.</span></span>  
  
 <span data-ttu-id="3f212-120">Pour une comparaison plus approfondie de LINQ to XML et des autres technologies XML Microsoft, consultez [LINQ to XML, différences par rapport à d’autres technologies XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).</span><span class="sxs-lookup"><span data-stu-id="3f212-120">For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. Other XML Technologies](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).</span></span>  
  
 <span data-ttu-id="3f212-121">XSLT est l'outil recommandé pour les transformations centrées sur les documents lorsque le document source a une structure irrégulière.</span><span class="sxs-lookup"><span data-stu-id="3f212-121">XSLT is the recommended tool for  document-centric transformations when the source document has an irregular structure.</span></span> <span data-ttu-id="3f212-122">Toutefois, LINQ to XML peut également effectuer des transformations centrées sur les documents.</span><span class="sxs-lookup"><span data-stu-id="3f212-122">However, LINQ to XML can also perform document-centric transforms.</span></span> <span data-ttu-id="3f212-123">Pour plus d’informations, consultez [Guide pratique pour utiliser des annotations pour transformer des arborescences LINQ to XML en un style XSLT (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md).</span><span class="sxs-lookup"><span data-stu-id="3f212-123">For more information, see [How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f212-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f212-124">See Also</span></span>  
 <span data-ttu-id="3f212-125">[Introduction aux transformations fonctionnelles pures (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="3f212-125">[Introduction to Pure Functional Transformations (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
 <span data-ttu-id="3f212-126">[Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) </span><span class="sxs-lookup"><span data-stu-id="3f212-126">[Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) </span></span>  
 [<span data-ttu-id="3f212-127">LINQ to XML, différences par rapport à d’autres technologies XML</span><span class="sxs-lookup"><span data-stu-id="3f212-127">LINQ to XML vs. Other XML Technologies</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)

