---
title: "Styles et mod&#232;les Expander | Microsoft Docs"
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
  - "ControlTemplate (WPF), Expander"
  - "Expander (WPF), styles et modèles"
  - "éléments (WPF), Expander"
  - "états (WPF), Expander"
  - "styles (WPF), Expander"
  - "modèles (WPF), Expander"
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Styles et mod&#232;les Expander
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Expander>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants d'Expander  
 Le contrôle <xref:System.Windows.Controls.Expander> ne comporte pas de composants nommés.  
  
## États d'Expander  
 Le tableau suivant répertorie les états visuels du contrôle <xref:System.Windows.Controls.Expander>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|Focused|FocusStates|Le contrôle a le focus.|  
|Unfocused|FocusStates|Le contrôle n'a pas le focus.|  
|Étendu|ExpansionStates|Le contrôle est développé.|  
|Collapsed|ExpansionStates|Le contrôle n'est pas développé.|  
|ExpandDown|ExpandDirectionStates|Le contrôle se développe vers le bas.|  
|ExpandUp|ExpandDirectionStates|Le contrôle se développe vers le haut.|  
|ExpandLeft|ExpandDirectionStates|Le contrôle se développe vers la gauche.|  
|ExpandRight|ExpandDirectionStates|Le contrôle se développe vers la droite.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Expander ControlTemplate, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Expander>.  
  
 [!code-xml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
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