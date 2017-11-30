---
title: "Comment : créer et utiliser une zone de dessin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8925b9b6cd6cea1a29592f591f9c1c89d32d49e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-a-canvas"></a>Comment : créer et utiliser une zone de dessin
Cet exemple montre comment créer et utiliser une instance de <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant positionne explicitement deux <xref:System.Windows.Controls.TextBlock> éléments à l’aide de la <xref:System.Windows.Controls.Canvas.SetTop%2A> et <xref:System.Windows.Controls.Canvas.SetLeft%2A> méthodes de <xref:System.Windows.Controls.Canvas>. L’exemple assigne également une <xref:System.Windows.Controls.Control.Background%2A> couleur de `LightSteelBlue` à la <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
>  Lorsque vous utilisez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] position <xref:System.Windows.Controls.TextBlock> éléments, utilisez le <xref:System.Windows.Controls.Canvas.Top%2A> et <xref:System.Windows.Controls.Canvas.Left%2A> propriétés.  
  
 [!code-csharp[CanvasCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.TextBlock>  
 <xref:System.Windows.Controls.Canvas.SetTop%2A>  
 <xref:System.Windows.Controls.Canvas.SetLeft%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)
