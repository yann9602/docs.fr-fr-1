---
title: "Entrée XPathDocument dans XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 80708dfa60636bbb038c3a86e336709339d2ac55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xpathdocument-input-to-xsltransform"></a><span data-ttu-id="372d1-102">Entrée XPathDocument dans XslTransform</span><span class="sxs-lookup"><span data-stu-id="372d1-102">XPathDocument Input to XslTransform</span></span>
<span data-ttu-id="372d1-103">L'objet <xref:System.Xml.XPath.XPathDocument> est un cache en lecture seule, destiné à traiter des documents avec l'objet <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="372d1-103">The <xref:System.Xml.XPath.XPathDocument> is a read-only cache, for processing documents with <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="372d1-104">Sa structure est analogue au DOM (Document Object Model) XML, mais elle est particulièrement optimisée pour le traitement XSLT (Extensible Stylesheet Language for Transformations) et le modèle de données XPath (XML Path Language) en utilisant les fonctions d'optimisation sur l'objet <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="372d1-104">It is structurally similar to the XML Document Object Model (DOM), but it is highly optimized for Extensible Stylesheet Language for Transformations (XSLT) processing and the XML Path Language (XPath) data model using the XPath optimization functions on the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="372d1-105">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="372d1-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="372d1-106">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="372d1-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="372d1-107">Consultez [à l’aide de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="372d1-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="372d1-108">L'exemple de code suivant crée un objet <xref:System.Xml.XPath.XPathDocument> en tant qu'entrée à transformer.</span><span class="sxs-lookup"><span data-stu-id="372d1-108">The following code sample creates an <xref:System.Xml.XPath.XPathDocument> as input to a transform.</span></span>  
  
```vb  
Dim xslt as XslTransform = new XslTransform()  
Xslt.Load(someStylesheet)  
Dim doc as XPathDocument = New XPathDocument("books.xml")  
Dim fs as StringWriter = new StringWriter()  
Xslt.Transform(doc, Nothing, fs, Nothing);  
```  
  
```csharp  
XslTransform xslt = new XslTransform();  
Xslt.Load(someStylesheet);  
XPathDocument doc = XPathDocument("books.xml");  
StringWriter fs = new StringWriter();  
Xslt.Transform(doc, null, fs, null);  
```  
  
## <a name="see-also"></a><span data-ttu-id="372d1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="372d1-109">See Also</span></span>  
 [<span data-ttu-id="372d1-110">XslTransform Class Implements the XSLT Processor</span><span class="sxs-lookup"><span data-stu-id="372d1-110">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
