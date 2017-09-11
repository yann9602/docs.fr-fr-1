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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7e1af87fceb9f3f7eae6af6f917037ba80908827
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="d84c7-102">Sérialisation vers un XmlReader (appel de XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d84c7-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="d84c7-103">Lorsque vous utilisez la <xref:System.Xml?displayProperty=fullName>capacités d’interopérabilité de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous pouvez utiliser <xref:System.Xml.Linq.XNode.CreateReader%2A>pour créer un <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XNode.CreateReader%2A> </xref:System.Xml?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d84c7-103">When you use the <xref:System.Xml?displayProperty=fullName> interoperability capabilities of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d84c7-104">Le module qui lit à partir de ce <xref:System.Xml.XmlReader>lit les nœuds de l’arborescence XML et les traite en conséquence.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="d84c7-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="d84c7-105">Appel d'une transformation XSLT</span><span class="sxs-lookup"><span data-stu-id="d84c7-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="d84c7-106">Une utilisation possible de cette méthode est lors de l'appel à une transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="d84c7-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="d84c7-107">Vous pouvez créer une arborescence XML, créer un <xref:System.Xml.XmlReader>à partir de l’arborescence XML, créer un nouveau document et créer un <xref:System.Xml.XmlWriter>pour écrire dans le nouveau document.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="d84c7-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="d84c7-108">Ensuite, vous pouvez appeler la transformation XSLT, en passant <xref:System.Xml.XmlReader>et <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="d84c7-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="d84c7-109">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="d84c7-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="d84c7-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d84c7-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d84c7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d84c7-111">See Also</span></span>  
 [<span data-ttu-id="d84c7-112">Sérialisation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d84c7-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
