---
title: "Comment&#160;: appliquer un FocusVisualStyle &#224; un contr&#244;le | Microsoft Docs"
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
  - "FocusVisualStyle (propriété)"
  - "propriétés, FocusVisualStyle"
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: appliquer un FocusVisualStyle &#224; un contr&#244;le
Cet exemple vous montre comment créer un style visuel de focus dans les ressources et appliquer le style à un contrôle, à l'aide de la propriété <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
## Exemple  
 L'exemple suivant définit un style qui crée une composition de contrôle supplémentaire qui s'applique uniquement lorsque ce contrôle porte sur le clavier dans l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  Cela est accompli en définissant un style avec un <xref:System.Windows.Controls.ControlTemplate>, puis en référençant ce style comme une ressource lors de la définition de la propriété <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Un rectangle externe ressemblant à une bordure est placé à l'extérieur de la zone rectangulaire.  À défaut de modification différente, le dimensionnement du style utilise le <xref:System.Windows.FrameworkElement.ActualHeight%2A> et le <xref:System.Windows.FrameworkElement.ActualWidth%2A> du contrôle rectangulaire où le style visuel de focus est appliqué.  Cet exemple définit des valeurs négatives pour le <xref:System.Windows.FrameworkElement.Margin%2A> pour que la bordure apparaisse légèrement à l'extérieur du contrôle ayant le focus.  
  
 [!code-xml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 Un <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> est additif pour tout style de modèle de contrôle provenant d'un style explicite ou d'un style de thème ; le style principal pour un contrôle peut encore être créé en utilisant un <xref:System.Windows.Controls.ControlTemplate> et en définissant ce style selon la propriété <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 Les styles visuels de focus doivent être utilisés régulièrement à travers un thème ou une interface utilisateur, plutôt que d'utiliser un style différent pour chaque élément pouvant être actif.  Pour plus d'informations, consultez [FocusVisualStyle et application d'un style au focus dans les contrôles](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [FocusVisualStyle et application d'un style au focus dans les contrôles](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)