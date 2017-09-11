---
title: "Récupération des paragraphes et leurs Styles (Visual Basic) | Documents Microsoft"
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
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d21ea826c8263ff391d4174ad1a7ebb173bb54d9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="5b7c5-102">Récupération des paragraphes et leurs Styles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b7c5-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="5b7c5-103">Dans cet exemple, nous écrivons une requête qui récupère les nœuds de paragraphe à partir d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="5b7c5-104">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="5b7c5-105">Cette requête est basée sur la requête dans l’exemple précédent, [recherche le Style de paragraphe par défaut (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), qui Récupère le style par défaut dans la liste des styles.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="5b7c5-106">Ces informations sont requises de manière que la requête puisse identifier le style des paragraphes pour lesquels aucun style n'est défini de façon explicite.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="5b7c5-107">Les style de paragraphes sont définis par le biais de l'élément `w:pPr` ; si un paragraphe ne contient pas cet élément, il est mis en forme avec le style par défaut.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="5b7c5-108">Cette rubrique explique l'importance de certaines parties de la requête, puis illustre la requête dans le cadre d'un exemple fonctionnel complet.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b7c5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b7c5-109">Example</span></span>  
 <span data-ttu-id="5b7c5-110">La source de la requête permettant de récupérer tous les paragraphes dans un document et leurs styles est la suivante :</span><span class="sxs-lookup"><span data-stu-id="5b7c5-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="5b7c5-111">Cette expression est similaire à la source de la requête dans l’exemple précédent, [recherche le Style de paragraphe par défaut (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="5b7c5-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="5b7c5-112">La principale différence est qu’elle utilise le <xref:System.Xml.Linq.XContainer.Descendants%2A>axe au lieu du <xref:System.Xml.Linq.XContainer.Elements%2A>axe.</xref:System.Xml.Linq.XContainer.Elements%2A> </xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="5b7c5-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="5b7c5-113">La requête utilise le <xref:System.Xml.Linq.XContainer.Descendants%2A>axe car dans les documents qui ont des sections, les paragraphes ne sera pas les enfants directs de l’élément de corps ; au lieu de cela, les paragraphes seront deux niveaux vers le bas dans la hiérarchie.</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="5b7c5-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="5b7c5-114">À l’aide de la <xref:System.Xml.Linq.XContainer.Descendants%2A>, le code fonctionnera ou non le document utilise des sections.</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="5b7c5-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b7c5-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b7c5-115">Example</span></span>  
 <span data-ttu-id="5b7c5-116">La requête utilise une clause `Let` afin de déterminer l'élément qui contient le nœud de style.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="5b7c5-117">S'il n'y a aucun élément, `styleNode` a la valeur `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="5b7c5-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="5b7c5-118">Le `Let` clause utilise d’abord le <xref:System.Xml.Linq.XContainer.Elements%2A>axes pour rechercher tous les éléments nommés `pPr`, puis utilise le <xref:System.Xml.Linq.Extensions.Elements%2A>méthode d’extension pour rechercher tous les éléments enfants nommés `pStyle`et pour finir utilise le <xref:System.Linq.Enumerable.FirstOrDefault%2A>opérateur de requête standard pour convertir la collection en singleton.</xref:System.Linq.Enumerable.FirstOrDefault%2A> </xref:System.Xml.Linq.Extensions.Elements%2A> </xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="5b7c5-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="5b7c5-119">Si la collection est vide, `styleNode` a la valeur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="5b7c5-120">Il s'agit d'un idiome utile pour rechercher le nœud descendant `pStyle`.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="5b7c5-121">Notez que si le nœud enfant `pPr` n'existe pas, le code n'échoue pas avec la levée d'une exception ; au lieu de cela, `styleNode` est définie à `Nothing`, ce qui constitue le comportement souhaité de cette clause `Let`.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="5b7c5-122">La requête projette une collection d'un type anonyme avec deux membres, `StyleName` et `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b7c5-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b7c5-123">Example</span></span>  
 <span data-ttu-id="5b7c5-124">Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphes à partir d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="5b7c5-125">Il identifie également le style de chaque paragraphe.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="5b7c5-126">Cet exemple se base sur les exemples précédents de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="5b7c5-127">Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="5b7c5-128">Vous trouverez des instructions pour la création du document source pour cet exemple, [création de la Source de Document Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="5b7c5-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="5b7c5-129">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="5b7c5-130">Il utilise des types dans le <xref:System.IO.Packaging?displayProperty=fullName>espace de noms.</xref:System.IO.Packaging?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5b7c5-130">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5b7c5-131">Cet exemple génère la sortie suivante lorsqu’appliqué au document décrit dans [création de la Source de Document Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="5b7c5-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="5b7c5-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5b7c5-132">Next Steps</span></span>  
 <span data-ttu-id="5b7c5-133">Dans la rubrique suivante, [récupération du texte des paragraphes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vous allez créer une requête pour récupérer le texte des paragraphes.</span><span class="sxs-lookup"><span data-stu-id="5b7c5-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b7c5-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b7c5-134">See Also</span></span>  
 [<span data-ttu-id="5b7c5-135">Didacticiel : Manipulation de contenu dans un Document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b7c5-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
