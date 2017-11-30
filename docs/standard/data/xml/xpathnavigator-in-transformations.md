---
title: XPathNavigator dans les transformations
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
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09f89708607ada18181bc6605994c7908e1dd14b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xpathnavigator-in-transformations"></a><span data-ttu-id="4b842-102">XPathNavigator dans les transformations</span><span class="sxs-lookup"><span data-stu-id="4b842-102">XPathNavigator in Transformations</span></span>
<span data-ttu-id="4b842-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit un accès aléatoire en lecture seule aux données et est destinée à être utilisée en tant qu'entrée dans XSLT (Extensible Stylesheet Language for Transformations).</span><span class="sxs-lookup"><span data-stu-id="4b842-103">The <xref:System.Xml.XPath.XPathNavigator> class provides read-only random access to data and is designed for use as an input to Extensible Stylesheet Language for Transformations (XSLT).</span></span> <span data-ttu-id="4b842-104">Elle est implémentée sur les objets <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument> et <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="4b842-104">It is implemented on the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, and <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="4b842-105">L'objet <xref:System.Xml.XPath.XPathNavigator> est basé sur le modèle de données du World Wide Web Consortium (W3C), comme indiqué dans la section 5 de la recommandation sur le langage XPath (XML Path Language).</span><span class="sxs-lookup"><span data-stu-id="4b842-105">The <xref:System.Xml.XPath.XPathNavigator> is based upon the World Wide Web Consortium (W3C) Data Model as described in section 5 of the XML Path Language (XPath) recommendation.</span></span>  
  
 <span data-ttu-id="4b842-106">L'objet <xref:System.Xml.XPath.XPathNavigator> définit un modèle de curseur sur n'importe quel magasin et fournit des requêtes XPath en lecture seule rapides sur un magasin de données.</span><span class="sxs-lookup"><span data-stu-id="4b842-106">The <xref:System.Xml.XPath.XPathNavigator> defines a cursor model over any store and provides fast, read-only XPath queries over any data store.</span></span> <span data-ttu-id="4b842-107"><xref:System.Xml.XPath.XPathNavigator> est également la classe à utiliser pour itérer sur des fragments d'arborescence résultat.</span><span class="sxs-lookup"><span data-stu-id="4b842-107">The <xref:System.Xml.XPath.XPathNavigator> is also the class to use for iterating over result tree fragments.</span></span>  
  
 <span data-ttu-id="4b842-108">L'API vous permet d'obtenir des informations à partir du nœud actuel dans le magasin et d'atteindre les nœuds connectés.</span><span class="sxs-lookup"><span data-stu-id="4b842-108">The API enables you to get information from the current node in the store and move to connected nodes.</span></span> <span data-ttu-id="4b842-109">Le <xref:System.Xml.XPath.XPathNavigator> est un modèle de style curseur qui parcourt un magasin à l’aide d’un ensemble de **déplacer** méthodes.</span><span class="sxs-lookup"><span data-stu-id="4b842-109">The <xref:System.Xml.XPath.XPathNavigator> is a cursor style model that performs traversal over a store using a set of **Move** methods.</span></span> <span data-ttu-id="4b842-110">La classe <xref:System.Xml.XPath.XPathNavigator> est toujours positionnée sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="4b842-110">The <xref:System.Xml.XPath.XPathNavigator> is always positioned on a node.</span></span> <span data-ttu-id="4b842-111">N’importe quel **déplacer** méthode qui échoue laisse le <xref:System.Xml.XPath.XPathNavigator> inchangée.</span><span class="sxs-lookup"><span data-stu-id="4b842-111">Any **Move** method that fails leaves the <xref:System.Xml.XPath.XPathNavigator> unchanged.</span></span>  
  
 <span data-ttu-id="4b842-112"><xref:System.Xml.XPath.XPathNavigator> est la classe à utiliser pour itérer sur des fragments d'arborescence résultat.</span><span class="sxs-lookup"><span data-stu-id="4b842-112">The <xref:System.Xml.XPath.XPathNavigator> is the class to use for iterating over result tree fragments.</span></span> <span data-ttu-id="4b842-113">L'exemple de code suivant crée un fragment d'arborescence résultat dans une feuille de style en appelant la fonction avec le paramètre `fragment` contenant du XML.</span><span class="sxs-lookup"><span data-stu-id="4b842-113">The following code sample creates a result tree fragment within a style sheet by calling the function with the parameter, `fragment`, which contains XML.</span></span>  
  
## <a name="testxsl"></a><span data-ttu-id="4b842-114">test.xsl</span><span class="sxs-lookup"><span data-stu-id="4b842-114">test.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl ="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
  
<xsl:variable name="fragment">  
    <authorlist>  
       <author>Joe</author>  
    </authorlist>  
</xsl:variable>  
  
<msxsl:script language="C#" implements-prefix="user">  
<![CDATA[  
   string NodeFragment(XPathNavigator nav)  
   {  
      if (nav.HasChildren)  
        return nav.Value;  
      else  
        return "";  
   }  
]]>  
</msxsl:script>  
  
<xsl:template match="/">  
     <xsl:value-of select="user:NodeFragment($fragment)"/>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a><span data-ttu-id="4b842-115">test.xml</span><span class="sxs-lookup"><span data-stu-id="4b842-115">test.xml</span></span>  
  
```xml  
<root>Some text</root>  
```  
  
 <span data-ttu-id="4b842-116">Le code suivant utilise la **test.xsl** feuille de style et **test.xml** les données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4b842-116">The following code uses the **test.xsl** style sheet and **test.xml** input data.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
Public Class sample  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load("test.xsl")  
  
        Dim xd As New XPathDocument("test.xml")  
  
        Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
        xslt.Transform(xd, Nothing, strmTemp, Nothing)  
    End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, null, strmTemp, null);  
    }  
}  
```  
  
## <a name="output"></a><span data-ttu-id="4b842-117">Sortie</span><span class="sxs-lookup"><span data-stu-id="4b842-117">Output</span></span>  
 <span data-ttu-id="4b842-118">Le résultat de la transformation se trouve dans le fichier **out.xml**:</span><span class="sxs-lookup"><span data-stu-id="4b842-118">The result of the transformation is found in the file **out.xml**:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b842-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b842-119">See Also</span></span>  
 [<span data-ttu-id="4b842-120">XslTransform Class Implements the XSLT Processor</span><span class="sxs-lookup"><span data-stu-id="4b842-120">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
