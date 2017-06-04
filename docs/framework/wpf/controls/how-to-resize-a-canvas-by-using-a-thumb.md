---
title: "Comment&#160;: redimensionner un Canvas &#224; l&#39;aide d&#39;un curseur | Microsoft Docs"
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
  - "Canvas (contrôle)"
  - "contrôles, Canvas"
  - "contrôles, Thumb"
  - "redimensionner un contrôle Canvas"
  - "Thumb (contrôle)"
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: redimensionner un Canvas &#224; l&#39;aide d&#39;un curseur
Cet exemple montre comment utiliser un contrôle <xref:System.Windows.Controls.Primitives.Thumb> pour redimensionner un contrôle <xref:System.Windows.Controls.Canvas>.  
  
## Exemple  
 Le contrôle <xref:System.Windows.Controls.Primitives.Thumb> fournit une fonctionnalité de glissement qui peut être utilisée pour déplacer ou redimensionner des contrôles en surveillant les événements <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> et <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> du <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 L'opération de glissement commence lorsque l'utilisateur appuie sur le bouton gauche de la souris au moment où le pointeur de la souris passe sur le contrôle <xref:System.Windows.Controls.Primitives.Thumb>.  L'opération de glissement continue jusqu'à ce que l'utilisateur relâche le bouton gauche de la souris.  Pendant l'opération de glissement, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> peut se produire plusieurs fois.  Chaque fois qu'il se produit, la classe <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> apporte la modification de position qui correspond à la modification de la position de la souris.  L'opération de glissement est terminée lorsque l'utilisateur relâche le bouton gauche de la souris.  L'opération de glissement ne fournit que de nouvelles coordonnées ; elle ne repositionne pas automatiquement le <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 L'exemple suivant montre un contrôle <xref:System.Windows.Controls.Primitives.Thumb>, élément enfant d'un contrôle <xref:System.Windows.Controls.Canvas>.  Le gestionnaire d'événements de son événement <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> fournit la logique pour déplacer le <xref:System.Windows.Controls.Primitives.Thumb> et redimensionner le <xref:System.Windows.Controls.Canvas>.  Les gestionnaires d'événements des événements <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> et <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> modifient la couleur du <xref:System.Windows.Controls.Primitives.Thumb> pendant une opération de glissement.  L'exemple suivant définit le <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 L'exemple suivant montre le gestionnaire d'événements <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> qui déplace le <xref:System.Windows.Controls.Primitives.Thumb> et redimensionne le <xref:System.Windows.Controls.Canvas>, suite au déplacement de la souris.  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 L'exemple suivant montre le gestionnaire d'événements <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 L'exemple suivant montre le gestionnaire d'événements <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Pour obtenir l'exemple complet, consultez [Fonctionnalité Glisser un curseur de défilement, exemple](http://go.microsoft.com/fwlink/?LinkID=160042).  
  
## Voir aussi  
 <xref:System.Windows.Controls.Primitives.Thumb>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>