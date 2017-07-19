---
title: "XPathNavigator dans les transformations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# XPathNavigator dans les transformations
La classe <xref:System.Xml.XPath.XPathNavigator> fournit un accès aléatoire en lecture seule aux données et est destinée à être utilisée en tant qu'entrée dans XSLT \(Extensible Stylesheet Language for Transformations\).  Elle est implémentée sur les objets <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument> et <xref:System.Xml.XmlDocument>.  L'objet <xref:System.Xml.XPath.XPathNavigator> est basé sur le modèle de données du World Wide Web Consortium \(W3C\), comme indiqué dans la section 5 de la recommandation sur le langage XPath \(XML Path Language\).  
  
 L'objet <xref:System.Xml.XPath.XPathNavigator> définit un modèle de curseur sur n'importe quel magasin et fournit des requêtes XPath en lecture seule rapides sur un magasin de données.  <xref:System.Xml.XPath.XPathNavigator> est également la classe à utiliser pour itérer sur des fragments d'arborescence résultat.  
  
 L'API vous permet d'obtenir des informations à partir du nœud actuel dans le magasin et d'atteindre les nœuds connectés.  L'objet <xref:System.Xml.XPath.XPathNavigator> est un modèle de style curseur qui parcourt un magasin à l'aide d'un ensemble de méthodes **Move**.  La classe <xref:System.Xml.XPath.XPathNavigator> est toujours positionnée sur un nœud.  Une méthode **Move** qui échoue laisse l'objet <xref:System.Xml.XPath.XPathNavigator> inchangé.  
  
 <xref:System.Xml.XPath.XPathNavigator> est la classe à utiliser pour itérer sur des fragments d'arborescence résultat.  L'exemple de code suivant crée un fragment d'arborescence résultat dans une feuille de style en appelant la fonction avec le paramètre `fragment` contenant du XML.  
  
## test.xsl  
  
```  
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
  
## test.xml  
  
```  
<root>Some text</root>  
```  
  
 Le code suivant utilise la feuille de style **test.xsl** et les données d'entrée **test.xml**.  
  
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
  
## Sortie  
 Le résultat de la transformation se trouve dans le fichier **out.xml** :  
  
```  
<?xml version="1.0" encoding="utf-8"?>Joe  
  
```  
  
## Voir aussi  
 [Implémentation du processeur XSLT par la classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)