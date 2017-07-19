---
title: "Comment&#160;: d&#233;terminer les param&#232;tres pris en charge par un encodeur | Microsoft Docs"
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
  - "paramètres d'encodeur, déterminer la prise en charge"
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: d&#233;terminer les param&#232;tres pris en charge par un encodeur
Vous pouvez ajuster les paramètres d'image, tels que la qualité et le niveau de compression, mais vous devez savoir quels paramètres sont pris en charge par un encodeur d'image donné.  La classe <xref:System.Drawing.Image> fournit la méthode <xref:System.Drawing.Image.GetEncoderParameterList%2A> afin que vous puissiez déterminer quels paramètres d'image sont pris en charge pour un encodeur spécifique.  Vous spécifiez l'encodeur avec un GUID.  La méthode <xref:System.Drawing.Image.GetEncoderParameterList%2A> retourne un tableau d'objets <xref:System.Drawing.Imaging.EncoderParameter>.  
  
## Exemple  
 L'exemple de code suivant présente les paramètres pris en charge pour l'encodeur JPEG.  Utilisez la liste des catégories de paramètre et les GUID associés dans la vue d'ensemble de la classe <xref:System.Drawing.Imaging.Encoder> pour déterminer la catégorie de chaque paramètre.  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Une application Windows Forms.  
  
-   <xref:System.Windows.Forms.PaintEventArgs>, un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Comment : répertorier les encodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)   
 [Types de bitmaps](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)   
 [Utilisation d'encodeurs et de décodeurs d'images dans GDI\+ managé](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)