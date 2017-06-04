---
title: "Styles et mod&#232;les ProgressBar | Microsoft Docs"
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
  - "ControlTemplate (WPF), ProgressBar"
  - "éléments (WPF), ProgressBar"
  - "ProgressBar (WPF), styles et modèles"
  - "états (WPF), ProgressBar"
  - "styles (WPF), ProgressBar"
  - "modèles (WPF), ProgressBar"
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Styles et mod&#232;les ProgressBar
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.ProgressBar>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de ProgressBar  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.ProgressBar>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_Indicator|<xref:System.Windows.FrameworkElement>|Objet qui indique la progression.|  
|PART\_Track|<xref:System.Windows.FrameworkElement>|Objet qui définit le chemin d'accès de l'indicateur de progression.|  
|PART\_GlowRect|<xref:System.Windows.FrameworkElement>|Objet qui embellit la barre de progression.|  
  
## États de ProgressBar  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.ProgressBar>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|---------------------|--------------------------|-----------------|  
|Determinate|CommonStates|<xref:System.Windows.Controls.ProgressBar> signale la progression en fonction de la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.|  
|Indeterminate|CommonStates|<xref:System.Windows.Controls.ProgressBar> signale la progression générale avec un modèle récurrent.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## ProgressBar ControlTemplate, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.ProgressBar>.  
  
 [!code-xml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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