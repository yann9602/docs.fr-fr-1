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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bb6d68296a720a796a319502c4cb2f0319727459
ms.lasthandoff: 03/13/2017


---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Récupération des paragraphes et leurs Styles (Visual Basic)
Dans cet exemple, nous écrivons une requête qui récupère les nœuds de paragraphe à partir d'un document WordprocessingML. Il identifie également le style de chaque paragraphe.  
  
 Cette requête est basée sur la requête dans l’exemple précédent, [recherche le Style de paragraphe par défaut (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), qui Récupère le style par défaut dans la liste des styles. Ces informations sont requises de manière que la requête puisse identifier le style des paragraphes pour lesquels aucun style n'est défini de façon explicite. Les style de paragraphes sont définis par le biais de l'élément `w:pPr` ; si un paragraphe ne contient pas cet élément, il est mis en forme avec le style par défaut.  
  
 Cette rubrique explique l'importance de certaines parties de la requête, puis illustre la requête dans le cadre d'un exemple fonctionnel complet.  
  
## <a name="example"></a>Exemple  
 La source de la requête permettant de récupérer tous les paragraphes dans un document et leurs styles est la suivante :  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Cette expression est similaire à la source de la requête dans l’exemple précédent, [recherche le Style de paragraphe par défaut (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). La principale différence est qu’elle utilise le <xref:System.Xml.Linq.XContainer.Descendants%2A>axe au lieu du <xref:System.Xml.Linq.XContainer.Elements%2A>axe.</xref:System.Xml.Linq.XContainer.Elements%2A> </xref:System.Xml.Linq.XContainer.Descendants%2A> La requête utilise le <xref:System.Xml.Linq.XContainer.Descendants%2A>axe car dans les documents qui ont des sections, les paragraphes ne sera pas les enfants directs de l’élément de corps ; au lieu de cela, les paragraphes seront deux niveaux vers le bas dans la hiérarchie.</xref:System.Xml.Linq.XContainer.Descendants%2A> À l’aide de la <xref:System.Xml.Linq.XContainer.Descendants%2A>, le code fonctionnera ou non le document utilise des sections.</xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
## <a name="example"></a>Exemple  
 La requête utilise une clause `Let` afin de déterminer l'élément qui contient le nœud de style. S'il n'y a aucun élément, `styleNode` a la valeur `Nothing` :  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 Le `Let` clause utilise d’abord le <xref:System.Xml.Linq.XContainer.Elements%2A>axes pour rechercher tous les éléments nommés `pPr`, puis utilise le <xref:System.Xml.Linq.Extensions.Elements%2A>méthode d’extension pour rechercher tous les éléments enfants nommés `pStyle`et pour finir utilise le <xref:System.Linq.Enumerable.FirstOrDefault%2A>opérateur de requête standard pour convertir la collection en singleton.</xref:System.Linq.Enumerable.FirstOrDefault%2A> </xref:System.Xml.Linq.Extensions.Elements%2A> </xref:System.Xml.Linq.XContainer.Elements%2A> Si la collection est vide, `styleNode` a la valeur `Nothing`. Il s'agit d'un idiome utile pour rechercher le nœud descendant `pStyle`. Notez que si le nœud enfant `pPr` n'existe pas, le code n'échoue pas avec la levée d'une exception ; au lieu de cela, `styleNode` est définie à `Nothing`, ce qui constitue le comportement souhaité de cette clause `Let`.  
  
 La requête projette une collection d'un type anonyme avec deux membres, `StyleName` et `ParagraphNode`.  
  
## <a name="example"></a>Exemple  
 Cet exemple traite un document WordprocessingML et récupère les nœuds de paragraphes à partir d'un document WordprocessingML. Il identifie également le style de chaque paragraphe. Cet exemple se base sur les exemples précédents de ce didacticiel. Dans le code ci-dessous, la nouvelle requête figure dans des commentaires.  
  
 Vous trouverez des instructions pour la création du document source pour cet exemple, [création de la Source de Document Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Cet exemple utilise des classes de l'assembly WindowsBase. Il utilise des types dans le <xref:System.IO.Packaging?displayProperty=fullName>espace de noms.</xref:System.IO.Packaging?displayProperty=fullName>  
  
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
  
 Cet exemple génère la sortie suivante lorsqu’appliqué au document décrit dans [création de la Source de Document Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans la rubrique suivante, [récupération du texte des paragraphes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), vous allez créer une requête pour récupérer le texte des paragraphes.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Manipulation de contenu dans un Document WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
