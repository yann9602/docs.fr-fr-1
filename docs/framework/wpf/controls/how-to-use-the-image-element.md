---
title: "Comment&#160;: utiliser l&#39;&#233;l&#233;ment Image | Microsoft Docs"
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
  - "BitmapImage (classe)"
  - "classes, BitmapImage"
  - "contrôles, Image"
  - "Image (contrôle)"
  - "restituer des images"
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: utiliser l&#39;&#233;l&#233;ment Image
Cet exemple indique comment inclure des images dans une application à l'aide de l'élément <xref:System.Windows.Controls.Image>.  
  
## Exemple  
 L'exemple suivant montre comment restituer une image de 200 pixels de large.  Dans cet exemple [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], la syntaxe d'attribut et de propriété Tag est utilisée pour définir l'image.  Pour plus d'informations sur la syntaxe d'attribut et la syntaxe de propriété, consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Un <xref:System.Windows.Media.Imaging.BitmapImage> est utilisé pour définir les données sources de l'image et est défini explicitement pour l'exemple de syntaxe de la propriété Tag.  De plus, le <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> du <xref:System.Windows.Media.Imaging.BitmapImage> a pour valeur la même largeur que le <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Controls.Image>.  Cela garantit que la quantité de mémoire minimale soit utilisée lors de la restitution de l'image.  
  
> [!NOTE]
>  En général, si vous souhaitez spécifier la taille d'une image rendue, indiquez uniquement le <xref:System.Windows.FrameworkElement.Width%2A> ou le <xref:System.Windows.FrameworkElement.Height%2A>, mais pas les deux à la fois.  Si vous en spécifiez un seulement, les [proportions](GTMT) de l'image sont conservées.  Sinon, l'image peut apparaître étirée ou déformée de façon inattendue.  Pour contrôler le comportement d'étirement de l'image, utilisez les propriétés <xref:System.Windows.Controls.Image.Stretch%2A> et <xref:System.Windows.Controls.Image.StretchDirection%2A>.  
  
> [!NOTE]
>  Lorsque vous spécifiez la taille d'une image avec <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A>, vous devez également affecter à <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> ou <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> la même taille respective.  
  
 La propriété <xref:System.Windows.Controls.Image.Stretch%2A> détermine comment la source d'image est étirée pour remplir l'élément d'image.  Pour plus d'informations, consultez l'énumération <xref:System.Windows.Media.Stretch>.  
  
 [!code-xml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## Exemple  
 L'exemple suivant montre comment restituer une image de 200 pixels de large à l'aide de code.  
  
> [!NOTE]
>  Les propriétés <xref:System.Windows.Media.Imaging.BitmapImage> doivent être définies dans un bloc <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> et <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## Voir aussi  
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)