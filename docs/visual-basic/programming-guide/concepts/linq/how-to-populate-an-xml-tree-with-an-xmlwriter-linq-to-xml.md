---
title: "Comment : remplir une arborescence XML avec un XmlWriter (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dfd10ec04e7293d90929d6f629201868028819ad
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Comment : remplir une arborescence XML avec un XmlWriter (LINQ to XML) (Visual Basic)
Permet de remplir une arborescence XML consiste à utiliser <xref:System.Xml.Linq.XContainer.CreateWriter%2A>pour créer un <xref:System.Xml.XmlWriter>, puis écrire dans le <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XContainer.CreateWriter%2A> L’arborescence XML est remplie avec tous les nœuds qui sont écrits dans le <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>  
  
 Vous utiliserez généralement cette méthode lorsque vous utilisez [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] avec une autre classe qui s’attend à écrire dans un <xref:System.Xml.XmlWriter>, tel que <xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform> </xref:System.Xml.XmlWriter>  
  
## <a name="example"></a>Exemple  
 Une utilisation possible de <xref:System.Xml.Linq.XContainer.CreateWriter%2A>est lors de l’appel d’une transformation XSLT.</xref:System.Xml.Linq.XContainer.CreateWriter%2A> Cet exemple crée une arborescence XML, crée un <xref:System.Xml.XmlReader>à partir de l’arborescence XML, crée un nouveau document, puis crée un <xref:System.Xml.XmlWriter>à écrire dans le nouveau document.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> Il appelle ensuite la transformation XSLT, en passant <xref:System.Xml.XmlReader>et <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.  
  
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
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A></xref:System.Xml.Linq.XContainer.CreateWriter%2A>   
 <xref:System.Xml.XmlWriter></xref:System.Xml.XmlWriter>   
 <xref:System.Xml.Xsl.XslCompiledTransform></xref:System.Xml.Xsl.XslCompiledTransform>   
 [Création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
