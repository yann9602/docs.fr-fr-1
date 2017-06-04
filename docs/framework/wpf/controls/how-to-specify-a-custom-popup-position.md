---
title: "Comment&#160;: sp&#233;cifier une position de menu contextuel personnalis&#233;e | Microsoft Docs"
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
  - "Popup (contrôle), spécifier une position personnalisée"
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: sp&#233;cifier une position de menu contextuel personnalis&#233;e
Cet exemple montre comment spécifier une position personnalisée pour un contrôle <xref:System.Windows.Controls.Primitives.Popup> lorsque la propriété <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a la valeur <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
## Exemple  
 Lorsque la propriété <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a la valeur <xref:System.Windows.Controls.Primitives.PlacementMode>, le <xref:System.Windows.Controls.Primitives.Popup> appelle une instance définie du délégué <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.  Ce délégué retourne un jeu de points possibles qui sont relatifs au coin supérieur gauche de la zone cible et au coin supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  L'emplacement du <xref:System.Windows.Controls.Primitives.Popup> a lieu au point qui fournit la meilleure visibilité.  
  
 L'exemple suivant montre comment définir la position d'un <xref:System.Windows.Controls.Primitives.Popup> en affectant <xref:System.Windows.Controls.Primitives.PlacementMode> à la propriété <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>.  Il indique également comment créer et assigner un délégué <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> afin de positionner le <xref:System.Windows.Controls.Primitives.Popup>.  Le délégué de rappel retourne deux objets <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>.  Si le <xref:System.Windows.Controls.Primitives.Popup> est masqué par un bord d'écran à la première position, le <xref:System.Windows.Controls.Primitives.Popup> est placé à la deuxième position.  
  
 [!code-xml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Pour obtenir l'exemple complet, consultez [Positionnement de Popup, exemple](http://go.microsoft.com/fwlink/?LinkID=160032).  
  
## Voir aussi  
 <xref:System.Windows.Controls.Primitives.Popup>   
 [Vue d'ensemble de Popup](../../../../docs/framework/wpf/controls/popup-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)