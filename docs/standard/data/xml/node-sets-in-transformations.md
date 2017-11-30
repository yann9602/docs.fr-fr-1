---
title: "Collections de nœuds dans les transformations"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d6d2f5a68ce5cef9937edc136e52efcd5366df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="c8d1a-102">Collections de nœuds dans les transformations</span><span class="sxs-lookup"><span data-stu-id="c8d1a-102">Node Sets in Transformations</span></span>
<span data-ttu-id="c8d1a-103">Les collections de nœuds correspondent à l'un des quatre types de données de base qui sont retournés à partir des expressions XPath (XML Path Language).</span><span class="sxs-lookup"><span data-stu-id="c8d1a-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="c8d1a-104">Une collection de nœuds, qui est une collection non triée de nœuds sans doublons, créée dans l'ordre du document, peut être attribué à une variable dans une feuille de style.</span><span class="sxs-lookup"><span data-stu-id="c8d1a-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8d1a-105">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8d1a-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="c8d1a-106">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c8d1a-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c8d1a-107">Consultez [à l’aide de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="c8d1a-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="c8d1a-108">Les collections de nœuds correspondent à l'un des quatre types de données de base qui sont retournés à partir des expressions XPath.</span><span class="sxs-lookup"><span data-stu-id="c8d1a-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="c8d1a-109">Une collection de nœuds, qui est une collection non triée de nœuds sans doublons, créée dans l'ordre du document, peut être attribué à une variable dans une feuille de style.</span><span class="sxs-lookup"><span data-stu-id="c8d1a-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="c8d1a-110">Cette collection de nœuds, qui résulte d'une expression XPath utilisée dans un attribut `select` dans une transformation, possède le même comportement qu'une collection de nœuds du DOM (Document Object Model) XML.</span><span class="sxs-lookup"><span data-stu-id="c8d1a-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="c8d1a-111">Vous pouvez accéder à un nœud à l’aide d’un ensemble de méthodes répertoriées dans [Node Set Navigation à l’aide de XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), contrairement à un fragment d’arborescence résultat ou un fragment d’arborescence résultat, qui utilise le <xref:System.Xml.XPath.XPathNodeIterator> pour la navigation.</span><span class="sxs-lookup"><span data-stu-id="c8d1a-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="c8d1a-112">L'exemple de code suivant montre comment itérer sur une collection de nœuds lorsqu'un élément `variable` ou `parameter` dans une feuille de style prend la valeur d'une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="c8d1a-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="c8d1a-113">Feuille de style</span><span class="sxs-lookup"><span data-stu-id="c8d1a-113">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="c8d1a-114">Entrée</span><span class="sxs-lookup"><span data-stu-id="c8d1a-114">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="c8d1a-115">Sortie</span><span class="sxs-lookup"><span data-stu-id="c8d1a-115">Output</span></span>  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8d1a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8d1a-116">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="c8d1a-117">Transformations XSLT avec la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="c8d1a-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="c8d1a-118">XslTransform Class Implements the XSLT Processor</span><span class="sxs-lookup"><span data-stu-id="c8d1a-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
