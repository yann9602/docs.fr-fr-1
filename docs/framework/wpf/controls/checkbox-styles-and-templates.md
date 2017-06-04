---
title: "Styles et mod&#232;les CheckBox | Microsoft Docs"
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
  - "CheckBox (WPF), styles et modèles"
  - "ControlTemplate (WPF), CheckBox"
  - "éléments (WPF), CheckBox"
  - "états (WPF), CheckBox"
  - "styles (WPF), CheckBox"
  - "modèles (WPF), CheckBox"
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Styles et mod&#232;les CheckBox
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.CheckBox>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants CheckBox  
 Le contrôle <xref:System.Windows.Controls.CheckBox> ne comporte pas de composants nommés.  
  
## États de CheckBox  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.CheckBox>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|---------------------|--------------------------|-----------------|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Pressed|CommonStates|Le contrôle est enfoncé.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|Focused|FocusStates|Le contrôle a le focus.|  
|Unfocused|FocusStates|Le contrôle n'a pas le focus.|  
|Activée|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `true`.|  
|Désactivée|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `false`.|  
|Indeterminate|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> a la valeur `true` et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> a la valeur `null`.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## CheckBox ControlTemplate, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.CheckBox>.  
  
 [!code-xml[ControlTemplateExamples#CheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
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