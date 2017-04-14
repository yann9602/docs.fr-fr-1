---
title: "Comment&#160;: utiliser des espaces de noms XML dans la liaison de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "liaison de données, espaces de noms XML"
  - "espaces de noms, XML"
  - "XML, espaces de noms"
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: utiliser des espaces de noms XML dans la liaison de donn&#233;es
## Exemple  
 Cet exemple montre comment gérer les espaces de noms spécifiés dans votre [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] [source de liaison](GTMT).  
  
 Si vos données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] possèdent la définition d'espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] suivante :  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 Vous pouvez utiliser l'élément <xref:System.Windows.Data.XmlNamespaceMapping> pour mapper l'espace de noms à un <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, comme dans l'exemple suivant.  Vous pouvez ensuite utiliser le <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> pour référencer l'espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  Le <xref:System.Windows.Controls.ListBox> de cette exemple affiche le *titre* et le *dc:date* de chaque *élément*.  
  
 [!code-xml[XmlnsBind#XmlNamespaceMapping](../../../../samples/snippets/xaml/VS_Snippets_Wpf/XmlnsBind/XAML/Window1.xaml#xmlnamespacemapping)]
 [!code-xml[XmlnsBind#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBind/CS/Window1.xaml#xmlnamespacemapping)]  
  
 Notez que le <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> spécifié ne doit pas correspondre à celui utilisé dans la source [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ; en cas de modification du préfixe dans la source [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], votre mappage fonctionne toujours.  
  
 Dans cet exemple, les données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] proviennent d'un service Web, mais l'élément <xref:System.Windows.Data.XmlNamespaceMapping> fonctionne aussi avec des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] inline ou les données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] d'un fichier incorporé.  
  
## Voir aussi  
 [Effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)