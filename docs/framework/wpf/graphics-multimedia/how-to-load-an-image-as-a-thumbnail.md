---
title: "Comment&#160;: charger une image en tant que miniature | Microsoft Docs"
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
  - "images, charger sous forme de miniatures"
  - "charger des images sous forme de miniatures"
  - "miniatures, charger des images sous forme de miniatures"
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: charger une image en tant que miniature
Les exemples suivants indiquent comment charger <xref:System.Windows.Controls.Image> en tant que miniature pour préserver la mémoire de l'application.  
  
## Exemple  
 L'exemple suivant définit la propriété <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> d'un <xref:System.Windows.Media.Imaging.BitmapImage> en langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] afin de diminuer la mémoire nécessaire au chargement de l'image.  
  
 [!code-xml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## Exemple  
 L'exemple suivant définit la propriété <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> d'un <xref:System.Windows.Media.Imaging.BitmapImage> dans le code afin de diminuer la mémoire nécessaire au chargement de l'image.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## Voir aussi  
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)