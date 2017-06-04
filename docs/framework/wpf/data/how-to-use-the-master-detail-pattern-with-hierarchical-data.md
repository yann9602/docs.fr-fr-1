---
title: "Comment&#160;: utiliser le mod&#232;le ma&#238;tre/d&#233;tail avec des donn&#233;es hi&#233;rarchiques | Microsoft Docs"
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
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: utiliser le mod&#232;le ma&#238;tre/d&#233;tail avec des donn&#233;es hi&#233;rarchiques
Cet exemple indique comment implémenter le scénario maître\/détail.  
  
## Exemple  
 Dans cet exemple, `LeagueList` est une collection de `Leagues`.  Chaque `League` a un `Name` et une collection de `Divisions` et chaque `Division` a un nom et une collection d'`Teams`.  Chaque `Team` a un nom d'équipe.  
  
 [!code-xml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 La capture d'écran suivante illustre l'exemple.  `Divisions`<xref:System.Windows.Controls.ListBox> suit automatiquement des sélections dans `Leagues`<xref:System.Windows.Controls.ListBox> et affiche les données correspondantes.  `Teams`<xref:System.Windows.Controls.ListBox> suit des sélections dans les deux autres contrôles <xref:System.Windows.Controls.ListBox>.  
  
 ![Exemple de détails principaux](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 Les deux choses à remarquer dans cet exemple sont :  
  
1.  Les trois contrôles <xref:System.Windows.Controls.ListBox> sont liés à la même source.  Vous devez définir la propriété <xref:System.Windows.Data.Binding.Path%2A> de la liaison pour spécifier le niveau de données affiché par <xref:System.Windows.Controls.ListBox>.  
  
2.  Vous devez affecter `true` à la propriété <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> sur les contrôles <xref:System.Windows.Controls.ListBox> dont vous suivez la sélection.  La définition de cette propriété garantit que l'élément sélectionné est toujours défini comme <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.  Ou bien, si <xref:System.Windows.Controls.ListBox> obtient ses données à partir de <xref:System.Windows.Data.CollectionViewSource>, celui\-ci synchronise automatiquement la sélection et la devise.  
  
 La technique est légèrement différente lorsque vous utilisez des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  Pour obtenir un exemple, consultez [Utiliser le modèle maître\/détail avec des données XML hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## Voir aussi  
 <xref:System.Windows.HierarchicalDataTemplate>   
 [Effectuer une liaison à une collection et afficher des informations basées sur la sélection](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)