---
title: Utilisation de XSLT pour transformer une arborescence XML (Visual Basic) | Documents Microsoft
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
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
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
ms.openlocfilehash: 860f6b9debae37059bb15ad6bb5de2ed6f9292cb
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a><span data-ttu-id="0df32-102">Utilisation de XSLT pour transformer une arborescence XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0df32-102">Using XSLT to Transform an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="0df32-103">Vous pouvez créer une arborescence XML, créer un <xref:System.Xml.XmlReader>à partir de l’arborescence XML, créer un nouveau document, puis créer un <xref:System.Xml.XmlWriter>qui écrira dans le nouveau document.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="0df32-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="0df32-104">Ensuite, vous pouvez appeler la transformation XSLT, en passant le <xref:System.Xml.XmlReader>et <xref:System.Xml.XmlWriter>à la transformation.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="0df32-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="0df32-105">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="0df32-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0df32-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="0df32-106">Example</span></span>  
  
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
  
Dim xmlTree As XElement = _   
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = _  
        New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="0df32-107">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0df32-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0df32-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0df32-108">See Also</span></span>  
 <span data-ttu-id="0df32-109"><xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0df32-109"><xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="0df32-110"><xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0df32-110"><xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="0df32-111"> [LINQ to XML (Visual Basic) de la programmation avancée](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)</span><span class="sxs-lookup"><span data-stu-id="0df32-111"> [Advanced LINQ to XML Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)</span></span>
