---
title: "Styles et mod&#232;les TextBox | Microsoft Docs"
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
  - "ControlTemplate (WPF), TextBox"
  - "éléments (WPF), TextBox"
  - "états (WPF), TextBox"
  - "styles (WPF), TextBox"
  - "modèles (WPF), TextBox"
  - "TextBox (WPF), styles et modèles"
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Styles et mod&#232;les TextBox
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.TextBox>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de TextBox  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.TextBox>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_ContentHost|<xref:System.Windows.FrameworkElement>|Élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>.  Le texte du <xref:System.Windows.Controls.TextBox> s'affiche dans cet élément.|  
  
## États de TextBox  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.TextBox>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|---------------------|--------------------------|-----------------|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|ReadOnly|CommonStates|L'utilisateur ne peut pas modifier le texte du <xref:System.Windows.Controls.TextBox>.|  
|Focused|FocusStates|Le contrôle a le focus.|  
|Unfocused|FocusStates|Le contrôle n'a pas le focus.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## TextBox ControlTemplate, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
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