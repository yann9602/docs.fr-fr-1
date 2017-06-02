---
title: "Utilisation de la classe XslCompiledTransform | Microsoft Docs"
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
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Utilisation de la classe XslCompiledTransform
La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le processeur XSLT dans Microsoft .NET Framework.  Cette classe est utilisée pour compiler des feuilles de style et exécuter des transformations XSLT.  
  
> [!NOTE]
>  Bien que les performances globales de la classe <xref:System.Xml.Xsl.XslCompiledTransform> soient meilleures que celles de la classe <xref:System.Xml.Xsl.XslTransform>, la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> de la classe <xref:System.Xml.Xsl.XslCompiledTransform> peut s'exécuter plus lentement que la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> de la classe <xref:System.Xml.Xsl.XslTransform> la première fois qu'elle est appelée pour une transformation.  C'est parce que le fichier XSLT doit être compilé avant d'être chargé.  Pour plus d'informations, consultez la publication de blog suivante : [XslCompiledTransform plus lent que XslTransform ?](http://go.microsoft.com/fwlink/?LinkId=130590)  
  
## Dans cette section  
 [Entrées dans la classe XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Décrit les options d'entrée XSLT disponibles.  
  
 [Options de sortie de la classe XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Décrit les options de sortie XSLT disponibles.  
  
 [Résolution de ressources externes lors du traitement XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Présente l'utilisation de la classe <xref:System.Xml.XmlResolver> pour résoudre des ressources externes.  
  
 [Extension de feuilles de style XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Présente la prise en charge des extensions XSLT.  
  
|||  
|-|-|  
|[Erreurs XSLT récupérables](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Répertorie chaque comportement discrétionnaire autorisé par la recommandation du World Wide Web Consortium \(W3C\) sur XSLT 1.0 et décrit la façon dont ces comportements sont gérés par la classe <xref:System.Xml.Xsl.XslCompiledTransform>.|  
|[Procédure : transformation d'un fragment de nœud](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Décrit comment transformer un fragment de nœud.|  
  
## Rubriques connexes  
 [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Explique comment migrer du code à partir de la classe <xref:System.Xml.Xsl.XslTransform>  
  
## Voir aussi  
 <xref:System.Xml.Xsl.XsltSettings>   
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>