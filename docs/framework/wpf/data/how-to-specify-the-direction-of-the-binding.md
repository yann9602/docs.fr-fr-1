---
title: "Comment&#160;: sp&#233;cifier le sens de la liaison | Microsoft Docs"
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
  - "direction de liaison"
  - "liaison de données, direction de liaison"
  - "direction de liaison"
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Comment&#160;: sp&#233;cifier le sens de la liaison
Cet exemple indique comment spécifier si la liaison met uniquement à jour la propriété [cible de liaison](GTMT) \(cible\), la propriété [source de liaison](GTMT) \(source\), ou à la fois les propriétés cible et source.  
  
## Exemple  
 Vous utilisez la propriété <xref:System.Windows.Data.Binding.Mode%2A> pour spécifier le sens de la liaison.  La liste d'énumération suivante affiche les options disponibles pour les mises à jour de liaison :  
  
-   <xref:System.Windows.Data.BindingMode> met à jour la propriété cible ou la propriété à chaque fois que la propriété cible ou source est modifiée.  
  
-   <xref:System.Windows.Data.BindingMode> met à jour la propriété cible uniquement lorsque la propriété source est modifiée.  
  
-   <xref:System.Windows.Data.BindingMode> met à jour la propriété cible uniquement lorsque l'application démarre ou lorsque le <xref:System.Windows.FrameworkElement.DataContext%2A> subit une modification.  
  
-   <xref:System.Windows.Data.BindingMode> met à jour la propriété source lorsque la propriété cible est modifiée.  
  
-   <xref:System.Windows.Data.BindingMode> entraîne l'utilisation de la valeur <xref:System.Windows.Data.Binding.Mode%2A> par défaut de la propriété cible.  
  
 Pour plus d'informations, consultez l'énumération <xref:System.Windows.Data.BindingMode>.  
  
 L'exemple suivant montre comment définir la propriété <xref:System.Windows.Data.Binding.Mode%2A>.  
  
 [!code-xml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Pour détecter des modifications de source \(applicables aux liaisons <xref:System.Windows.Data.BindingMode> et <xref:System.Windows.Data.BindingMode>\), la source doit implémenter un mécanisme de notification des modifications de propriétés approprié tel que <xref:System.ComponentModel.INotifyPropertyChanged>.  Consultez [Implémenter la notification des modifications de propriétés](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) pour obtenir un exemple d'implémentation de <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Pour les liaisons <xref:System.Windows.Data.BindingMode> ou <xref:System.Windows.Data.BindingMode>, vous pouvez contrôler le minutage des mises à jour de la source en définissant la propriété <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  Pour plus d'informations, consultez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## Voir aussi  
 <xref:System.Windows.Data.Binding>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)