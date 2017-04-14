---
title: "Vue d&#39;ensemble des mod&#232;les et styles d&#39;en-t&#234;te de colonne GridView | Microsoft Docs"
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
  - "en-têtes de colonnes, personnaliser"
  - "contrôles, ListView"
  - "GridView (mode d'affichage), personnaliser des en-têtes de colonnes"
  - "en-têtes, personnaliser"
  - "contrôles ListView (WPF), GridView (styles d'en-tête de colonne)"
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble des mod&#232;les et styles d&#39;en-t&#234;te de colonne GridView
Cette vue d'ensemble traite de l'ordre de priorité des propriétés que vous utilisez pour personnaliser un en\-tête de colonne dans le mode d'affichage <xref:System.Windows.Controls.GridView> d'un contrôle <xref:System.Windows.Controls.ListView>.  
  
## Personnalisation d'un en\-tête de colonne dans un GridView  
 On trouve les propriétés qui définissent le contenu, la disposition et le style d'un en\-tête de colonne dans un <xref:System.Windows.Controls.GridView> dans de nombreuses classes connexes.  Certaines de ces propriétés ont des fonctionnalités semblables ou identiques.  
  
 Les lignes du tableau suivant affichent des groupes de propriétés qui exécutent la même fonction.  Vous pouvez utiliser ces propriétés pour personnaliser les en\-têtes de colonnes dans un <xref:System.Windows.Controls.GridView>.  L'ordre de priorité des propriétés connexes est défini de droite à gauche ; la propriété de la colonne la plus à droite a la priorité la plus élevée.  Par exemple, si un <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> est défini sur l'objet <xref:System.Windows.Controls.GridViewColumnHeader> et le <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> est défini sur la <xref:System.Windows.Controls.GridViewColumn> associée, le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a la priorité.  Dans ce scénario, le <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> n'a aucun effet.  
  
 **Propriétés connexes pour les en\-têtes de colonnes dans un GridView**  
  
|||||  
|-|-|-|-|  
|**Classes**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**Propriétés du menu contextuel**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|Non applicable|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**ToolTip**<br /><br /> **Propriétés**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|Non applicable|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**Modèle d'en\-tête**<br /><br /> **Propriétés**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**Propriétés de style**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>Pour les **propriétés du modèle d'en\-tête**, si vous définissez le modèle et les propriétés du sélecteur du modèle, la propriété du modèle a la priorité.  Par exemple, si vous définissez les propriétés <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> et <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>, la propriété <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a la priorité.  
  
## Voir aussi  
 [Rubriques Comment](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)