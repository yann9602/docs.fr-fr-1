---
title: "Comment&#160;: personnaliser la taille du curseur sur une barre de d&#233;filement | Microsoft Docs"
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
  - "personnaliser la taille du curseur"
  - "ScrollBar (contrôle)"
  - "curseur (taille)"
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: personnaliser la taille du curseur sur une barre de d&#233;filement
Cette rubrique explique comment affecter au <xref:System.Windows.Controls.Primitives.Thumb> d'un <xref:System.Windows.Controls.Primitives.ScrollBar> une taille fixe et comment spécifier la taille minimum du <xref:System.Windows.Controls.Primitives.Thumb> d'un <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## Exemple  
  
## Description  
 L'exemple suivant crée un <xref:System.Windows.Controls.Primitives.ScrollBar> dont le <xref:System.Windows.Controls.Primitives.Thumb> a une taille fixe.  L'exemple affecte à la propriété <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> du <xref:System.Windows.Controls.Primitives.Thumb> la valeur <xref:System.Double.NaN> et définit la hauteur du <xref:System.Windows.Controls.Primitives.Thumb>.  Pour créer un <xref:System.Windows.Controls.Primitives.ScrollBar> horizontal avec un <xref:System.Windows.Controls.Primitives.Thumb> de taille fixe, définissez la largeur du <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## Code  
 [!code-xml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## Description  
 L'exemple suivant crée un <xref:System.Windows.Controls.Primitives.ScrollBar> dont le <xref:System.Windows.Controls.Primitives.Thumb> a une taille minimale.  L'exemple définit la valeur de <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.  Pour créer un <xref:System.Windows.Controls.Primitives.ScrollBar> horizontal pour lequel <xref:System.Windows.Controls.Primitives.Thumb> a une largeur minimum, définissez <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## Code  
 [!code-xml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## Voir aussi  
 [Styles et modèles ScrollBar](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)