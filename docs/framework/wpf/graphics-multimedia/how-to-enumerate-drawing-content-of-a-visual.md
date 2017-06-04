---
title: "Comment&#160;: &#233;num&#233;rer le contenu de dessin d&#39;un Visual | Microsoft Docs"
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
  - "énumérer le contenu d'un Visual (WPF)"
  - "récupérer la valeur DrawingGroup d'un Visual (WPF)"
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# Comment&#160;: &#233;num&#233;rer le contenu de dessin d&#39;un Visual
L'objet <xref:System.Windows.Media.Drawing> fournit un modèle objet pour l'énumération du contenu d'un <xref:System.Windows.Media.Visual>.  
  
## Exemple  
 L'exemple suivant utilise la méthode <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> pour récupérer la valeur <xref:System.Windows.Media.DrawingGroup> d'un <xref:System.Windows.Media.Visual> et l'énumérer.  
  
> [!NOTE]
>  Lorsque vous énumérez le contenu d'un visuel, vous récupérez des objets <xref:System.Windows.Media.Drawing>, et non pas la représentation sous\-jacente des données rendues comme liste d'instructions graphiques vectorielles.  Pour plus d'informations, consultez [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## Voir aussi  
 <xref:System.Windows.Media.Drawing>   
 <xref:System.Windows.Media.DrawingGroup>   
 <xref:System.Windows.Media.VisualTreeHelper>   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)