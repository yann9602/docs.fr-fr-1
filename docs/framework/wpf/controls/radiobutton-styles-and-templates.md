---
title: "Styles et mod&#232;les RadioButton | Microsoft Docs"
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
  - "ControlTemplate (WPF), RadioButton"
  - "éléments (WPF), RadioButton"
  - "RadioButton (WPF), styles et modèles"
  - "états (WPF), RadioButton"
  - "styles (WPF), RadioButton"
  - "modèles (WPF), RadioButton"
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Styles et mod&#232;les RadioButton
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.RadioButton>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de RadioButton  
 Le contrôle <xref:System.Windows.Controls.RadioButton> ne comporte pas de composants nommés.  
  
## États de RadioButton  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.RadioButton>.  
  
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
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## RadioButton ControlTemplate, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.RadioButton>.  
  
 [!code-xml[ControlTemplateExamples#RadioButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
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