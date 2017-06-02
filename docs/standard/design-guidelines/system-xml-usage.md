---
title: "Utilisation de System.Xml | Microsoft Docs"
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
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# Utilisation de System.Xml
Cette section présente l’utilisation de plusieurs types résidant dans <xref:System.Xml?displayProperty=fullName> espaces de noms qui peut être utilisé pour représenter les données XML.  
  
 **X ne pas** utiliser <xref:System.Xml.XmlNode> ou <xref:System.Xml.XmlDocument> pour représenter les données XML. Favoriser l’utilisation d’instances de <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ou un sous\-type de <xref:System.Xml.Linq.XNode> à la place.`XmlNode` et `XmlDocument` ne sont pas conçus pour l’exposition des API publiques.  
  
 **✓ faire** utiliser `XmlReader`, `IXPathNavigable`, ou un sous\-type de `XNode` en tant qu’entrée ou sortie de membres qui acceptent ou renvoient des données XML.  
  
 Utilisez ces abstractions au lieu de `XmlDocument`, `XmlNode`, ou <xref:System.Xml.XPath.XPathDocument>, car cela dissocie les méthodes à partir des implémentations spécifiques de document XML en mémoire et leur permet de travailler avec les sources de données XML virtuels qui exposent `XNode`, `XmlReader`, ou <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X ne pas** sous\-classe `XmlDocument` Si vous souhaitez créer un type qui représente une vue XML d’une source de données ou le modèle objet sous\-jacent.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications relatives à l'utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)