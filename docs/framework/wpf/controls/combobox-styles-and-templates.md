---
title: "Styles et mod&#232;les ComboBox | Microsoft Docs"
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
  - "ComboBox (WPF), styles et modèles"
  - "ControlTemplate (WPF), ComboBox"
  - "éléments (WPF), ComboBox"
  - "états (WPF), ComboBox"
  - "styles (WPF), ComboBox"
  - "modèles (WPF), ComboBox"
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Styles et mod&#232;les ComboBox
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ComboBox>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de ComboBox  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.ComboBox>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_EditableTextBox|<xref:System.Windows.Controls.TextBox>|Contient le texte de <xref:System.Windows.Controls.ComboBox>.|  
|PART\_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Menu déroulant qui contient les éléments de la zone de liste déroulante.|  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour <xref:System.Windows.Controls.ComboBox>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>.  \(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément de <xref:System.Windows.Controls.ComboBox> ; <xref:System.Windows.Controls.ScrollViewer> active le défilement dans le contrôle.\)  Si <xref:System.Windows.Controls.ItemsPresenter> n'est pas l'enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer à <xref:System.Windows.Controls.ItemsPresenter> le nom `ItemsPresenter`.  
  
## États de ComboBox  
 Le tableau ci\-dessous répertorie les états du contrôle <xref:System.Windows.Controls.ComboBox>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris se trouve sur le contrôle <xref:System.Windows.Controls.ComboBox>.|  
|Focused|FocusStates|Le contrôle a le focus.|  
|Unfocused|FocusStates|Le contrôle n'a pas le focus.|  
|FocusedDropDown|FocusStates|Le menu déroulant du contrôle <xref:System.Windows.Controls.ComboBox> a le focus.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
|Editable|EditStates|La propriété <xref:System.Windows.Controls.ComboBox.IsEditable%2A> est `true`.|  
|Uneditable|EditStates|La propriété <xref:System.Windows.Controls.ComboBox.IsEditable%2A> est `false`.|  
  
## Composants de ComboBoxItem  
 Le contrôle <xref:System.Windows.Controls.ComboBoxItem> ne comporte pas de composants nommés.  
  
## États de ComboBoxItem  
 Le tableau ci\-dessous répertorie les états du contrôle <xref:System.Windows.Controls.ComboBoxItem>.  
  
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
  
## ComboBox ControlTemplate, exemple  
 L'exemple suivant indique comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ComboBox> et ses types associés.  
  
 [!code-xml[ControlTemplateExamples#ComboBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
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