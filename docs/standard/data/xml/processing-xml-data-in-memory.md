---
title: "Traitement de donn&#233;es XML en m&#233;moire | Microsoft Docs"
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
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# Traitement de donn&#233;es XML en m&#233;moire
Le Microsoft .NET Framework comprend trois modèles pour le traitement des données XML : la classe <xref:System.Xml.XmlDocument>, la classe <xref:System.Xml.XPath.XPathDocument> et [LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 La classe <xref:System.Xml.XmlDocument> implémente les recommandations du W3C relatives aux modèles objet de document \(DOM\), niveaux 1 et 2 \(noyau\).  Le DOM est une représentation sous la forme d'une arborescence \(cache\) en mémoire d'un document XML.  L'objet <xref:System.Xml.XmlDocument> et les classes y afférentes permettent de construire des documents XML, de charger et d'accéder à des données, de modifier des données et d'enregistrer des modifications.  
  
 La classe <xref:System.Xml.XPath.XPathDocument> est un magasin de données en mémoire en lecture seule basé sur le modèle de données XPath.  La classe <xref:System.Xml.XPath.XPathNavigator> propose plusieurs options de modification et fonctionnalités de navigation à l'aide d'un modèle de curseur entre des documents XML contenus dans la classe <xref:System.Xml.XPath.XPathDocument> en lecture seule ainsi que dans la classe <xref:System.Xml.XmlDocument>.  
  
 [LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md) est le nouveau modèle du .NET Framework version 3.5 pour le traitement des données XML.  Il s'agit d'un modèle de traitement en mémoire qui se base sur [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  LINQ étend la syntaxe des langages C\# et Visual Basic pour fournir de nouvelles capacités de requête.  
  
## Dans cette section  
 [Traitement de données XML à l'aide du modèle DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Explique l'utilisation de l'objet <xref:System.Xml.XmlDocument> et des classes y afférentes pour le traitement de données XML.  
  
 [Traitement des données XML à l'aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Explique l'utilisation des classes <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> et <xref:System.Xml.XPath.XPathNavigator> pour le traitement de données XML.  
  
 [Traitement des données XML à l'aide de LINQ to XML](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 Fournit une brève vue d'ensemble de LINQ to XML et indique des liens vers la documentation LINQ to XML.  
  
## Rubriques connexes  
 [Documents et données XML](../../../../docs/standard/data/xml/index.md)