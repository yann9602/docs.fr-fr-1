---
title: "Comment&#160;: choisir entre StackPanel et DockPanel | Microsoft Docs"
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
  - "contrôles (WPF), DockPanel"
  - "contrôles (WPF), StackPanel"
  - "DockPanel (contrôle), comparaison avec le contrôle StackPanel"
  - "StackPanel (contrôle), comparaison avec le contrôle DockPanel"
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: choisir entre StackPanel et DockPanel
Cet exemple montre comment choisir entre utiliser <xref:System.Windows.Controls.StackPanel> ou <xref:System.Windows.Controls.DockPanel> pour empiler du contenu dans un <xref:System.Windows.Controls.Panel>.  
  
## Exemple  
 Bien qu'il soit possible d'utiliser <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.StackPanel> pour empiler des éléments enfants, les deux contrôles ne produisent pas toujours les mêmes résultats.  Par exemple, l'ordre dans lequel vous placez les éléments enfants peut affecter la taille des éléments enfants dans <xref:System.Windows.Controls.DockPanel> mais pas dans <xref:System.Windows.Controls.StackPanel>.  Cette différence de comportement se produit car <xref:System.Windows.Controls.StackPanel> mesure dans le sens de l'empilement au niveau de <xref:System.Double.PositiveInfinity>.<xref:System.Double> alors que <xref:System.Windows.Controls.DockPanel> ne mesure que la taille disponible.  
  
 L'exemple suivant montre cette différence clé entre <xref:System.Windows.Controls.DockPanel> et <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.StackPanel>   
 <xref:System.Windows.Controls.DockPanel>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)