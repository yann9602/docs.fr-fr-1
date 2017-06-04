---
title: "Comment&#160;: utiliser le mod&#232;le ma&#238;tre/d&#233;tail avec des donn&#233;es XML hi&#233;rarchiques | Microsoft Docs"
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
  - "liaison de données, maître/détail (paradigme de données)"
  - "maître/détail (paradigme de données)"
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: utiliser le mod&#232;le ma&#238;tre/d&#233;tail avec des donn&#233;es XML hi&#233;rarchiques
Cet exemple indique comment implémenter le scénario maître\/détail avec des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
## Exemple  
 Cet exemple correspond à la version des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] de l'exemple décrit dans [Utiliser le modèle maître\/détail avec des données hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  Dans cet exemple, les données proviennent du fichier `League.xml`.  Notez comment le troisième contrôle <xref:System.Windows.Controls.ListBox> suit les modifications de sélection dans le second <xref:System.Windows.Controls.ListBox> en se liant à sa propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.  
  
 [!code-xml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## Voir aussi  
 <xref:System.Windows.HierarchicalDataTemplate>   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)