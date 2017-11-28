---
title: Utilisation de XSLT pour transformer une arborescence XML (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0abd857def00bd1e96332cd635d49aa50b2b873b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="604f4-102">Utilisation de XSLT pour transformer une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="604f4-102">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="604f4-103">Vous pouvez créer une arborescence XML, créer un objet <xref:System.Xml.XmlReader> à partir de l'arborescence XML, créer un nouveau document, puis créer un objet <xref:System.Xml.XmlWriter> qui écrira dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="604f4-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="604f4-104">Ensuite, vous pouvez appeler la transformation XSLT, en passant le <xref:System.Xml.XmlReader> et le <xref:System.Xml.XmlWriter> à la transformation.</span><span class="sxs-lookup"><span data-stu-id="604f4-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="604f4-105">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="604f4-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="604f4-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="604f4-106">Example</span></span>  
  
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
  
    // Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="604f4-107">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="604f4-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="604f4-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="604f4-108">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="604f4-109">Programmation LINQ to XML avancée (C#)</span><span class="sxs-lookup"><span data-stu-id="604f4-109">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
