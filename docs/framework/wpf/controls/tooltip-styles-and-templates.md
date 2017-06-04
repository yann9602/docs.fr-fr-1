---
title: "Styles et mod&#232;les ToolTip | Microsoft Docs"
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
  - "ControlTemplate (WPF), Info-bulle"
  - "éléments (WPF), Info-bulle"
  - "états (WPF), Info-bulle"
  - "styles (WPF), Info-bulle"
  - "modèles (WPF), Info-bulle"
  - "ToolTip (WPF), styles et modèles"
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Styles et mod&#232;les ToolTip
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ToolTip>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Éléments de ToolTip  
 Le contrôle <xref:System.Windows.Controls.ToolTip> ne comporte pas de composants nommés.  
  
## États de ToolTip  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.ToolTip>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Closed|OpenStates|État par défaut.|  
|Ouvrez .|OpenStates|<xref:System.Windows.Controls.ToolTip> est visible.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## ToolTip ControlTemplate, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ToolTip>.  
  
 [!code-xml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
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