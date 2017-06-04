---
title: "Styles et mod&#232;les ScrollBar | Microsoft Docs"
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
  - "ControlTemplate (WPF), ScrollBar"
  - "éléments (WPF), ScrollBar"
  - "ScrollBar (WPF), styles et modèles"
  - "états (WPF), ScrollBar"
  - "styles (WPF), ScrollBar"
  - "modèles (WPF), ScrollBar"
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Styles et mod&#232;les ScrollBar
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de ScrollBar  
 Le tableau suivant répertorie les composants nommés du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_Track|<xref:System.Windows.Controls.Primitives.Track>|Conteneur de cet élément indiquant la position de <xref:System.Windows.Controls.Primitives.ScrollBar>.|  
  
## États de ScrollBar  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|---------------------|--------------------------|-----------------|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## ScrollBar ControlTemplate, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 [!code-xml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
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