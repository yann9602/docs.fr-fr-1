---
title: Transformations XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d7fa8492487daff68fd8ebaf4159dd537d13e51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-transformations"></a>Transformations XSLT
Les transformations XSLT (Extensible Stylesheet Language Transformation) ont pour but de transformer le contenu d'un document XML source en un autre document dont le format ou la structure diffère. Par exemple, vous pouvez utiliser XSLT pour transformer un document XML en un document HTML pour une utilisation sur un site web ou en un document qui contient uniquement les champs requis par une application. Ce processus de transformation est spécifié par le [recommandation W3C XSL Transformations (XSLT) Version 1.0](http://go.microsoft.com/fwlink/?LinkID=49919).  
  
 La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le processeur XSLT dans le .NET Framework. La classe <xref:System.Xml.Xsl.XslCompiledTransform> prend en charge la recommandation du W3C sur XSLT 1.0.  
  
> [!NOTE]
>  La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le .NET Framework version 2.0. La classe <xref:System.Xml.Xsl.XslCompiledTransform> est une nouvelle implémentation du moteur XSLT. Elle inclut des améliorations de performances et de nouvelles fonctions de sécurité. La pratique recommandée consiste à créer des applications XSLT à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [À l’aide de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 Fournit des informations sur l'utilisation de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 [Migration à partir de la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Explique comment migrer du code à partir de la classe <xref:System.Xml.Xsl.XslTransform>.  
  
 [Compilateur XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 Fournit des informations sur l'utilisation de XSLT Compiler.  
  
 [Transformations XSLT avec la classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 Fournit des informations sur l'utilisation de la classe <xref:System.Xml.Xsl.XslTransform>.  
  
 **Remarque** la <xref:System.Xml.Xsl.XslTransform> classe est obsolète dans la .NET Framework version 2.0.  
  
## <a name="reference"></a>Référence  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Documents et données XML](../../../../docs/standard/data/xml/index.md)
