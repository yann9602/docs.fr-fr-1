---
title: "Comment&#160;: rogner une image | Microsoft Docs"
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
  - "classes, CroppedBitmap"
  - "CroppedBitmap (classe)"
  - "rogner des images"
  - "images, rogner"
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: rogner une image
Cet exemple indique comment rogner une image à l'aide de <xref:System.Windows.Media.Imaging.CroppedBitmap>.  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> est principalement utilisé lors de l'encodage de la version rognée d'une image à enregistrer dans un fichier.  Pour rogner une image à des fins d'affichage, consultez la rubrique [Create a Clip Region](http://msdn.microsoft.com/fr-fr/56e4bed6-78d7-4292-b917-d72d0b3e4376).  
  
## Exemple  
 Le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivant définit les ressources utilisées dans les exemples ci\-dessous.  
  
 [!code-xml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 L'exemple suivant crée une image en utilisant un <xref:System.Windows.Media.Imaging.CroppedBitmap> comme source.  
  
 [!code-xml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 Le <xref:System.Windows.Media.Imaging.CroppedBitmap> peut également être utilisé comme source d'un autre <xref:System.Windows.Media.Imaging.CroppedBitmap>, en chaînant le rognage.  Notez que le <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> utilise des valeurs qui sont relatives au bitmap source rogné et non à l'image initiale.  
  
 [!code-xml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## Voir aussi  
 [Create a Clip Region](http://msdn.microsoft.com/fr-fr/56e4bed6-78d7-4292-b917-d72d0b3e4376)