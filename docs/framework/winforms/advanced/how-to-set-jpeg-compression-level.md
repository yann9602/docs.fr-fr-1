---
title: "Comment&#160;: d&#233;finir le niveau de compression JPEG | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "images (Windows Forms), modifier les paramètres de l'encodeur"
  - "JPEG (images), définir le niveau de qualité"
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: d&#233;finir le niveau de compression JPEG
Vous pouvez modifier les paramètres d'une image lorsque vous enregistrez l'image sur disque pour réduire la taille de fichier ou améliorer sa qualité.  Vous pouvez ajuster la qualité d'une image JPEG en modifiant son niveau de compression.  Pour spécifier le niveau de compression lorsque vous enregistrez une image JPEG, vous devez créer un objet <xref:System.Drawing.Imaging.EncoderParameters> et le passer à la méthode <xref:System.Drawing.Image.Save%2A> de la classe <xref:System.Drawing.Image>.  Initialisez l'objet <xref:System.Drawing.Imaging.EncoderParameters> afin qu'il ait un tableau composé d'un <xref:System.Drawing.Imaging.EncoderParameter>.  Lorsque vous créez le <xref:System.Drawing.Imaging.EncoderParameter>, spécifiez l'encodeur <xref:System.Drawing.Imaging.Encoder.Quality> et le niveau de compression souhaité.  
  
## Exemple  
 L'exemple de code suivant crée un objet <xref:System.Drawing.Imaging.EncoderParameter> et enregistre trois images JPEG.  Chaque image JPEG est enregistrée avec un niveau de qualité différent, en modifiant la valeur `long` passée au constructeur <xref:System.Drawing.Imaging.EncoderParameter>.  Un niveau de qualité de 0 correspond à la plus grande compression, et un niveau de qualité de 100 correspond à la compression minimale.  
  
 [!code-csharp[UsingImageEncodersDecoders#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#8)]
 [!code-vb[UsingImageEncodersDecoders#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#8)]  
[!code-csharp[UsingImageEncodersDecoders#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#6)]
[!code-vb[UsingImageEncodersDecoders#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#6)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Une application Windows Forms.  
  
-   <xref:System.Windows.Forms.PaintEventArgs>, un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
-   Un fichier image nommé `TestPhoto.jpg` et situé sous **c:\\**.  
  
## Voir aussi  
 [Comment : déterminer les paramètres pris en charge par un encodeur](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)   
 [Types de bitmaps](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)   
 [Utilisation d'encodeurs et de décodeurs d'images dans GDI\+ managé](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)