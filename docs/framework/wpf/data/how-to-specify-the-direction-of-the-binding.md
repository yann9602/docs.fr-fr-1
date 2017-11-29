---
title: "Comment : spécifier le sens de la liaison"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdcda02a61f0114bfbbe5d5c411cb397cddcf683
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Comment : spécifier le sens de la liaison
Cet exemple montre comment spécifier si la liaison met à jour uniquement la propriété de la cible de liaison (cible), uniquement la propriété de la source de liaison (source), ou bien à la fois la propriété cible et la propriété source.  
  
## <a name="example"></a>Exemple  
 Vous utilisez le <xref:System.Windows.Data.Binding.Mode%2A> propriété pour spécifier la direction de la liaison. La liste d’énumération suivante affiche les options disponibles pour les mises à jour de la liaison :  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay>met à jour la propriété cible ou la propriété chaque fois que la propriété cible ou la propriété source change.  
  
-   <xref:System.Windows.Data.BindingMode.OneWay>met à jour la propriété cible uniquement lorsque la propriété source change.  
  
-   <xref:System.Windows.Data.BindingMode.OneTime>met à jour la propriété cible uniquement lorsque l’application démarre ou lorsque le <xref:System.Windows.FrameworkElement.DataContext%2A> subit une modification.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource>met à jour la propriété source lorsque la propriété cible change.  
  
-   <xref:System.Windows.Data.BindingMode.Default>provoque la valeur par défaut <xref:System.Windows.Data.Binding.Mode%2A> valeur de propriété cible à utiliser.  
  
 Pour plus d’informations, consultez l’énumération <xref:System.Windows.Data.BindingMode>.  
  
 L'exemple suivant indique comment définir la propriété <xref:System.Windows.Data.Binding.Mode%2A>.  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Pour détecter des modifications de source (applicables aux <xref:System.Windows.Data.BindingMode.OneWay> et <xref:System.Windows.Data.BindingMode.TwoWay> liaisons), la source doit implémenter un mécanisme de notification de modification de propriété approprié tel que <xref:System.ComponentModel.INotifyPropertyChanged>. Consultez [Notification de modification de propriété implémentez](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) pour obtenir un exemple d’un <xref:System.ComponentModel.INotifyPropertyChanged> mise en œuvre.  
  
 Pour <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> liaisons, vous pouvez contrôler le minutage des mises à jour des source en définissant le <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriété. Pour plus d'informations, voir <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.Binding>  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
