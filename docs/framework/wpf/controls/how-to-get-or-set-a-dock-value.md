---
title: "Comment&#160;: obtenir ou d&#233;finir une valeur Dock | Microsoft Docs"
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
  - "valeurs Dock, obtenir"
  - "valeurs Dock, définir"
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: obtenir ou d&#233;finir une valeur Dock
L'exemple suivant montre comment assigner une valeur <xref:System.Windows.Controls.Dock> à un objet.  L'exemple utilise les méthodes <xref:System.Windows.Controls.DockPanel.GetDock%2A> et <xref:System.Windows.Controls.DockPanel.SetDock%2A> du <xref:System.Windows.Controls.DockPanel>.  
  
## Exemple  
 L'exemple crée une instance de l'élément <xref:System.Windows.Controls.TextBlock>, `txt1` et assigne une valeur <xref:System.Windows.Controls.Dock> de `Top` à l'aide de la méthode <xref:System.Windows.Controls.DockPanel.SetDock%2A> de <xref:System.Windows.Controls.DockPanel>.  Il ajoute ensuite la valeur de la propriété <xref:System.Windows.Controls.Dock> au <xref:System.Windows.Controls.TextBlock.Text%2A> de l'élément <xref:System.Windows.Controls.TextBlock> à l'aide de la méthode <xref:System.Windows.Controls.DockPanel.GetDock%2A>.  Pour finir, l'exemple ajoute l'élément <xref:System.Windows.Controls.TextBlock> au <xref:System.Windows.Controls.DockPanel>, `dp1` parent.  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.DockPanel>   
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>   
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)