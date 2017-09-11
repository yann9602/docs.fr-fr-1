---
title: "Vue d’ensemble de la classe XElement (Visual Basic) | Documents Microsoft"
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
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
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
ms.openlocfilehash: 78a72effa021408943b9248546106c6fd655ac0b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="52966-102">Vue d’ensemble de la classe XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52966-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="52966-103">La <xref:System.Xml.Linq.XElement>classe est une des classes fondamentales dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="52966-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span> <span data-ttu-id="52966-104">Elle représente un élément XML.</span><span class="sxs-lookup"><span data-stu-id="52966-104">It represents an XML element.</span></span> <span data-ttu-id="52966-105">Vous pouvez utiliser cette classe pour créer des éléments, modifier le contenu de l'élément, ajouter, modifier ou supprimer des éléments enfants, ajouter des attributs à un élément ou sérialiser le contenu d'un élément sous forme textuelle.</span><span class="sxs-lookup"><span data-stu-id="52966-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="52966-106">Vous pouvez également interagir avec d’autres classes dans <xref:System.Xml?displayProperty=fullName>, tel que <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>et <xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform> </xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> </xref:System.Xml?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="52966-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=fullName>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="52966-107">Fonctionnalité de XElement</span><span class="sxs-lookup"><span data-stu-id="52966-107">XElement Functionality</span></span>  
 <span data-ttu-id="52966-108">Cette rubrique décrit les fonctionnalités fournies par la <xref:System.Xml.Linq.XElement>classe.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="52966-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="52966-109">Construction d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="52966-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="52966-110">Vous pouvez construire des arborescences XML de diverses façons, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="52966-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="52966-111">Vous pouvez construire une arborescence XML dans du code.</span><span class="sxs-lookup"><span data-stu-id="52966-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="52966-112">Pour plus d’informations, consultez [création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="52966-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="52966-113">Vous pouvez analyser les données XML provenant de diverses sources, y compris un <xref:System.IO.TextReader>, fichiers texte, ou une adresse Web (URL).</xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="52966-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="52966-114">Pour plus d’informations, consultez [l’analyse de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="52966-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="52966-115">Vous pouvez utiliser un <xref:System.Xml.XmlReader>pour remplir l’arborescence.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="52966-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="52966-116">Pour plus d’informations, consultez <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="52966-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="52966-117">Si vous avez un module qui peut écrire du contenu dans une <xref:System.Xml.XmlWriter>, vous pouvez utiliser la <xref:System.Xml.Linq.XContainer.CreateWriter%2A>méthode pour créer un writer, passer ce dernier au module, puis utiliser le contenu qui est écrite dans le <xref:System.Xml.XmlWriter>pour remplir l’arborescence XML.</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XContainer.CreateWriter%2A> </xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="52966-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="52966-118">Toutefois, la manière la plus courante de créer une arborescence XML est la suivante :</span><span class="sxs-lookup"><span data-stu-id="52966-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="52966-119">Une autre technique de création d’une arborescence XML très courante implique l’utilisation des résultats d’une [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requête pour remplir une arborescence XML, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="52966-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="52966-120">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="52966-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="52966-121">Sérialisation d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="52966-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="52966-122">Vous pouvez sérialiser l’arborescence XML vers un <xref:System.IO.File>, un <xref:System.IO.TextWriter>, ou un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="52966-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="52966-123">Pour plus d’informations, consultez [sérialiser des arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="52966-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="52966-124">Récupération de données XML par le biais de méthodes d'axe</span><span class="sxs-lookup"><span data-stu-id="52966-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="52966-125">Vous pouvez utiliser des méthodes d'axe pour récupérer des attributs, des éléments enfants, des éléments descendants et des éléments ancêtres.</span><span class="sxs-lookup"><span data-stu-id="52966-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="52966-126">Les requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] opèrent sur les méthodes d'axe et offrent plusieurs moyens flexibles et puissants de parcourir et de traiter une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="52966-126">[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="52966-127">Pour plus d’informations, consultez [Axes LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="52966-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="52966-128">Interrogation d’arborescences XML</span><span class="sxs-lookup"><span data-stu-id="52966-128">Querying XML Trees</span></span>  
 <span data-ttu-id="52966-129">Vous pouvez écrire [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requêtes qui extraient des données à partir d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="52966-129">You can write [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="52966-130">Pour plus d’informations, consultez [interroger des arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="52966-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="52966-131">Modification d’arborescences XML</span><span class="sxs-lookup"><span data-stu-id="52966-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="52966-132">Vous pouvez modifier un élément de différentes façons, y compris modifier son contenu ou ses attributs.</span><span class="sxs-lookup"><span data-stu-id="52966-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="52966-133">Vous pouvez également supprimer un élément de son parent.</span><span class="sxs-lookup"><span data-stu-id="52966-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="52966-134">Pour plus d’informations, consultez [modification d’arborescences XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="52966-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52966-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52966-135">See Also</span></span>  
 [<span data-ttu-id="52966-136">LINQ to XML programmation présentation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52966-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
