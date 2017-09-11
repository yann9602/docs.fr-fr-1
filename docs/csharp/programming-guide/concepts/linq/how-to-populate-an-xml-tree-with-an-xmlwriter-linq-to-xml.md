---
title: Guide pratique pour remplir une arborescence XML avec un XmlWriter (LINQ to XML) (C#)
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
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9d74e6bd3d8454f5ed37fa8d190beb0c44399fa7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="2ef7e-102">Guide pratique pour remplir une arborescence XML avec un XmlWriter (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2ef7e-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2ef7e-103">L'une des manières de remplir une arborescence XML consiste à utiliser <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un objet <xref:System.Xml.XmlWriter>, puis à écrire dans l'objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="2ef7e-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="2ef7e-104">L'arborescence XML est remplie avec tous les nœuds écrits dans l'objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="2ef7e-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="2ef7e-105">Cette méthode est généralement utilisée quand [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est employé avec une autre classe censée écrire dans un objet <xref:System.Xml.XmlWriter>, tel que <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="2ef7e-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ef7e-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ef7e-106">Example</span></span>  
 <span data-ttu-id="2ef7e-107">Une utilisation possible de <xref:System.Xml.Linq.XContainer.CreateWriter%2A> est lors de l'appel à une transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="2ef7e-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="2ef7e-108">Cet exemple crée une arborescence XML, crée un objet <xref:System.Xml.XmlReader> à partir de l'arborescence XML, crée un nouveau document, puis crée un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="2ef7e-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="2ef7e-109">Il appelle ensuite la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="2ef7e-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="2ef7e-110">Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.</span><span class="sxs-lookup"><span data-stu-id="2ef7e-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
using (XmlWriter writer = newTree.CreateWriter())  
{  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="2ef7e-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2ef7e-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ef7e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ef7e-112">See Also</span></span>  
 <span data-ttu-id="2ef7e-113"><xref:System.Xml.Linq.XContainer.CreateWriter%2A></span><span class="sxs-lookup"><span data-stu-id="2ef7e-113"><xref:System.Xml.Linq.XContainer.CreateWriter%2A></span></span>   
 <span data-ttu-id="2ef7e-114"><xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="2ef7e-114"><xref:System.Xml.XmlWriter></span></span>   
 <span data-ttu-id="2ef7e-115"><xref:System.Xml.Xsl.XslCompiledTransform></span><span class="sxs-lookup"><span data-stu-id="2ef7e-115"><xref:System.Xml.Xsl.XslCompiledTransform></span></span>   
 [<span data-ttu-id="2ef7e-116">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2ef7e-116">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

