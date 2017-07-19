---
title: "Styles et mod&#232;les TreeView | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ControlTemplate (WPF), TreeView"
  - "éléments (WPF), TreeView"
  - "états (WPF), TreeView"
  - "styles (WPF), TreeView"
  - "modèles (WPF), TreeView"
  - "TreeView (WPF), styles et modèles"
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Styles et mod&#232;les TreeView
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.TreeView>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de TreeView  
 Le contrôle <xref:System.Windows.Controls.TreeView> ne comporte pas de composants nommés.  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour <xref:System.Windows.Controls.TreeView>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>.  \(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément de <xref:System.Windows.Controls.TreeView> ; <xref:System.Windows.Controls.ScrollViewer> active le défilement dans le contrôle.\)  Si <xref:System.Windows.Controls.ItemsPresenter> n'est pas l'enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer à <xref:System.Windows.Controls.ItemsPresenter> le nom `ItemsPresenter`.  
  
## États de TreeView  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.TreeView>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Composants de TreeViewItem  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.TreeViewItem>.  
  
|Élément|Type|Description|  
|-------------|----------|-----------------|  
|PART\_Header|<xref:System.Windows.FrameworkElement>|Élément visuel qui contient le contenu de l'en\-tête du contrôle <xref:System.Windows.Controls.TreeView>.|  
  
## États de TreeViewItem  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.TreeViewItem>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|---------------------|--------------------------|-----------------|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur <xref:System.Windows.Controls.TreeViewItem>.|  
|Disabled|CommonStates|<xref:System.Windows.Controls.TreeViewItem> est désactivé.|  
|Focused|FocusStates|<xref:System.Windows.Controls.TreeViewItem> a le focus.|  
|Unfocused|FocusStates|<xref:System.Windows.Controls.TreeViewItem> n'a pas le focus.|  
|Étendu|ExpansionStates|Le contrôle <xref:System.Windows.Controls.TreeViewItem> est développé.|  
|Collapsed|ExpansionStates|Le contrôle <xref:System.Windows.Controls.TreeViewItem> est réduit.|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> a des éléments.|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> n'a pas d'éléments.|  
|Sélectionné|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> est sélectionné.|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> est sélectionné mais n'est pas actif.|  
|Non sélectionné|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> n'est pas sélectionné.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## TreeView ControlTemplate, exemple  
 L'exemple suivant indique comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.TreeView> et ses types associés.  
  
 [!code-xml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 L'exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour l'exemple complet, consultez          [Style avec ControlTemplates, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160041) .  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)