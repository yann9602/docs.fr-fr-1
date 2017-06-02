---
title: "Styles et mod&#232;les ListView | Microsoft Docs"
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
  - "ControlTemplate (WPF), ListView"
  - "ListView (WPF), styles et modèles"
  - "éléments (WPF), ListView"
  - "états (WPF), ListView"
  - "styles (WPF), ListView"
  - "modèles (WPF), ListView"
ms.assetid: d2387356-2171-4785-822a-7247e024b4ee
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Styles et mod&#232;les ListView
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ListView>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de ListView  
 Le contrôle <xref:System.Windows.Controls.ListView> ne comporte pas de composants nommés.  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour <xref:System.Windows.Controls.ListView>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>.  \(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément de <xref:System.Windows.Controls.ListView> ; <xref:System.Windows.Controls.ScrollViewer> active le défilement dans le contrôle.\)  Si <xref:System.Windows.Controls.ItemsPresenter> n'est pas l'enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer à <xref:System.Windows.Controls.ItemsPresenter> le nom `ItemsPresenter`.  
  
## États de ListView  
 Le tableau suivant répertorie les états visuels du contrôle <xref:System.Windows.Controls.ListView>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Composants de ListViewItem  
 Le contrôle <xref:System.Windows.Controls.ListViewItem> ne comporte pas de composants nommés.  
  
## États de ListViewItem  
 Le tableau ci\-dessous répertorie les états du contrôle <xref:System.Windows.Controls.ListViewItem>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris se trouve sur le contrôle <xref:System.Windows.Controls.ComboBox>.|  
|Focused|FocusStates|Le contrôle a le focus.|  
|Unfocused|FocusStates|Le contrôle n'a pas le focus.|  
|Sélectionné|SelectionStates|L'élément est actuellement sélectionné.|  
|Non sélectionné|SelectionStates|L'élément n'est pas sélectionné.|  
|SelectedUnfocused|SelectionStates|L'élément est sélectionné, mais n'a pas focus.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## ListView ControlTemplate, exemples  
 L'exemple suivant indique comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ListView> et ses types associés.  
  
 [!code-xml[ControlTemplateExamples#ListView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 L'exemple <xref:System.Windows.Controls.ControlTemplate> utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour l'exemple complet, consultez [Style avec ControlTemplates, exemple](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)