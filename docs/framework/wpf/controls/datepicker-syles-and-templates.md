---
title: "Styles et mod&#232;les DatePicker | Microsoft Docs"
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
  - "ControlTemplate (WPF), DatePicker"
  - "DatePicker (WPF), styles et modèles"
  - "éléments (WPF), DatePicker"
  - "états (WPF), DatePicker"
  - "styles (WPF), DatePicker"
  - "modèles (WPF), DatePicker"
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Styles et mod&#232;les DatePicker
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.DatePicker>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de DatePicker  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.DatePicker>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_Root|<xref:System.Windows.Controls.Grid>|Racine du contrôle.|  
|PART\_Button|<xref:System.Windows.Controls.Button>|Bouton qui ouvre et ferme le <xref:System.Windows.Controls.Calendar>.|  
|PART\_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Zone de texte qui vous permet d'entrer une date.|  
|PART\_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Menu contextuel du contrôle <xref:System.Windows.Controls.DatePicker>.|  
  
## États de DatePicker  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.DatePicker>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|Disabled|CommonStates|<xref:System.Windows.Controls.DatePicker> est désactivé.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Composants de DatePickerTextBox  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_Watermark|<xref:System.Windows.Controls.ContentControl>|Élément qui contient le texte initial dans <xref:System.Windows.Controls.DatePicker>.|  
|PART\_ContentElement|<xref:System.Windows.FrameworkElement>|Élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>.  Le texte du <xref:System.Windows.Controls.TextBox> s'affiche dans cet élément.|  
  
## États de DatePickerTextBox  
 Le tableau suivant répertorie les états visuels du contrôle <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|L'utilisateur ne peut pas modifier le texte du <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Focused|FocusStates|Le contrôle a le focus.|  
|Unfocused|FocusStates|Le contrôle n'a pas le focus.|  
|Watermarked|WatermarkStates|Le contrôle affiche son texte d'origine.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> est dans cet état lorsque l'utilisateur n'a pas entré de texte ou sélectionné de date.|  
|Unwatermarked|WatermarkStates|L'utilisateur a entré du texte dans <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ou sélectionné une date dans <xref:System.Windows.Controls.DatePicker>.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## DatePicker ControlTemplate, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.DatePicker>.  
  
 [!code-xml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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