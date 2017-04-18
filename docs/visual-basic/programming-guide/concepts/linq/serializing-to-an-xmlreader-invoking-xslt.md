---
title: "Sérialisation vers un XmlReader (appel de XSLT) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bca1e63bbe5b3ccd13f183c3cc6081917624ad94
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>Sérialisation vers un XmlReader (appel de XSLT) (Visual Basic)
Lorsque vous utilisez la <xref:System.Xml?displayProperty=fullName>capacités d’interopérabilité de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous pouvez utiliser <xref:System.Xml.Linq.XNode.CreateReader%2A>pour créer un <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XNode.CreateReader%2A> </xref:System.Xml?displayProperty=fullName> Le module qui lit à partir de ce <xref:System.Xml.XmlReader>lit les nœuds de l’arborescence XML et les traite en conséquence.</xref:System.Xml.XmlReader>  
  
## <a name="invoking-an-xslt-transformation"></a>Appel d'une transformation XSLT  
 Une utilisation possible de cette méthode est lors de l'appel à une transformation XSLT. Vous pouvez créer une arborescence XML, créer un <xref:System.Xml.XmlReader>à partir de l’arborescence XML, créer un nouveau document et créer un <xref:System.Xml.XmlWriter>pour écrire dans le nouveau document.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> Ensuite, vous pouvez appeler la transformation XSLT, en passant <xref:System.Xml.XmlReader>et <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>  
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
