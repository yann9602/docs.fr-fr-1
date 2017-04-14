---
title: "Options de traitement XML | Microsoft Docs"
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
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# Options de traitement XML
Reportez\-vous aux tableaux suivants pour obtenir une liste des technologies Microsoft que vous pouvez utiliser pour traiter des données XML.  
  
## Options du .NET Framework  
  
|**Option**|**Type de traitement**|**Description**|  
|----------------|----------------------------|---------------------|  
|[LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <br /> \(\(espace de noms <xref:System.Xml.Linq>\)|En mémoire|-   Basé sur la technologie LINQ \(Langage\-Integrated Query\) du .NET Framework.<br />-   Fournit une expérience de requête similaire à SQL pour les objets, les données relationnelles et les données XML.<br />-   Fournit des fonctionnalités de création et de transformation de documents intuitives.<br />-   Utilisez cette option si vous écrivez un nouveau code.|  
|<xref:System.Xml.XmlReader?displayProperty=fullName>|Basé sur les flux|-   Fournit un accès rapide, en avant seulement et non mis en cache aux données XML.<br />-   Vous pouvez créer des objets à l'aide de la méthode <xref:System.Xml.XmlReader.Create%2A?displayProperty=fullName> et spécifier l'ensemble de fonctionnalités à activer sur l'objet avec la classe <xref:System.Xml.XmlReaderSettings>.|  
|<xref:System.Xml.XmlWriter?displayProperty=fullName>|Basé sur les flux|-   Fournit un moyen rapide, en avant seulement et non mis en cache de générer des données XML.<br />-   Vous pouvez créer des objets à l'aide de la méthode <xref:System.Xml.XmlWriter.Create%2A?displayProperty=fullName> et spécifier l'ensemble de fonctionnalités à activer sur l'objet avec la classe <xref:System.Xml.XmlWriterSettings>.|  
|<xref:System.Xml.XmlDocument?displayProperty=fullName>|En mémoire|-   Implémente les recommandations [W3C Document Object Model \(DOM\) Level 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/) et [DOM Level 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/).<br />-   Vous pouvez créer, insérer, supprimer et modifier des nœuds à l'aide de méthodes et de propriétés basées sur le modèle DOM habituel.<br />-   Utilisez cette option si vous modifiez du code existant qui implémente le modèle W3C DOM.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=fullName>|En mémoire|-   Offre plusieurs options d'édition et capacités de navigation utilisant un modèle de curseur.<br />-   Les documents XML peuvent être contenus dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.<br />-   Procure d'excellentes performances pour le traitement en lecture seule du code XML.<br />-   Utilisez cette option si vous modifiez du code existant à l'aide de requêtes XPath ou de transformations XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|En mémoire|-   Fournit des options pour la transformation de données XML à l'aide des transformations XSL.<br />-   Le [XSLT Compiler \(xsltc.exe\)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) vous permet de faire référence à des transformations précompilées dans votre application.|  
  
## Options Win32 et COM  
  
|**Option**|**Description**|  
|----------------|---------------------|  
|[XmlLite](http://go.microsoft.com/fwlink/?LinkId=93723)|-   Analyseur XML rapide, sécurisé, sans mise en cache et avant uniquement qui vous permet de créer des applications XML hautes performances.<br />-   Fonctionne avec n'importe quel langage capable d'utiliser des bibliothèques de liens dynamiques \(DLL\). Nous recommandons l'utilisation de C\+\+.|  
|[MSXML](http://go.microsoft.com/fwlink/?LinkId=93722)|-   Technologie compatible COM pour le traitement du code XML, qui est fournie avec le système d'exploitation Windows.<br />-   Fournit une implémentation native du modèle DOM avec prise en charge de XPath et XSLT.<br />-   Inclut l'analyseur basé sur les événements SAX2.|  
  
## Voir aussi  
 [Traitement de données XML à l'aide du modèle DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)   
 [Traitement des données XML à l'aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)   
 [XSLT Compiler \(xsltc.exe\)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)