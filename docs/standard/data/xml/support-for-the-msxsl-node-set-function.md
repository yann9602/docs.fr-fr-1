---
title: "Prise en charge de la fonction msxsl:node-set() | Microsoft Docs"
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
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Prise en charge de la fonction msxsl:node-set()
La fonction `msxsl:node-set` vous permet de convertir un fragment d'arborescence résultat en une collection de nœuds.  La collection de nœuds obtenue contient toujours un seul nœud et représente le nœud racine de l'arborescence.  
  
> [!NOTE]
>  La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  Vous pouvez effectuer des transformations XSLT \(Extensible Stylesheet Language Transformation\) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 La fonction `msxsl:node-set` vous permet de convertir un fragment d'arborescence résultat en une collection de nœuds.  La collection de nœuds obtenue contient toujours un seul nœud et représente le nœud racine de l'arborescence.  
  
## Exemple  
 Dans l'exemple suivant, `$var` est une variable qui est une arborescence de nœuds dans la feuille de style.  L'instruction for\-each associée à la fonction `node-set` permet à l'utilisateur d'itérer sur cette arborescence de nœuds comme une collection de nœuds.  
  
## nodeset.xsl  
  
```  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/)</author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## Sortie  
 La sortie de la transformation est :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## Voir aussi  
 [Implémentation du processeur XSLT par la classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)