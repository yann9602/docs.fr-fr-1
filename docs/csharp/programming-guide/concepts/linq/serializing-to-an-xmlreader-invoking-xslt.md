---
title: "Sérialisation vers un XmlReader (appel de XSLT) (C#) | Microsoft Docs"
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
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 96fed09349264710dc8f0591a0022939e9a4181a
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>Sérialisation vers un XmlReader (appel de XSLT) (C#)
Lorsque vous utilisez les capacités d’interopérabilité <xref:System.Xml?displayProperty=fullName> de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous pouvez utiliser <xref:System.Xml.Linq.XNode.CreateReader%2A> pour créer un <xref:System.Xml.XmlReader>. Le module qui lit à partir de cet objet <xref:System.Xml.XmlReader> lit les nœuds issus de l’arborescence XML et les traite en conséquence.  
  
## <a name="invoking-an-xslt-transformation"></a>Appel d'une transformation XSLT  
 Une utilisation possible de cette méthode est lors de l'appel à une transformation XSLT. Vous pouvez créer une arborescence XML, créer un <xref:System.Xml.XmlReader> à partir de l’arborescence XML, créer un document, puis créer un <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document. Ensuite, vous pouvez appeler la transformation XSLT, en lui passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>. Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
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
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
