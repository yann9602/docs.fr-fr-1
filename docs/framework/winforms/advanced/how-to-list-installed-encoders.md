---
title: "Comment&#160;: r&#233;pertorier les encodeurs install&#233;s | Microsoft Docs"
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
  - "codecs d'image, répertorier"
  - "encodeurs d'image, répertorier"
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: r&#233;pertorier les encodeurs install&#233;s
Vous pouvez répertorier les encodeurs d'images disponibles sur un ordinateur afin de déterminer si votre application peut enregistrer dans un format de fichier d'image spécifique.  La classe <xref:System.Drawing.Imaging.ImageCodecInfo> fournit les méthodes statiques <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> permettant de déterminer les encodeurs d'image disponibles.  <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> retourne un tableau d'objets <xref:System.Drawing.Imaging.ImageCodecInfo>.  
  
## Exemple  
 L'exemple de code suivant présente la liste des encodeurs installés et leurs valeurs de propriété.  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Une application Windows Forms.  
  
-   <xref:System.Windows.Forms.PaintEventArgs>, un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Comment : répertorier les décodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)   
 [Utilisation d'encodeurs et de décodeurs d'images dans GDI\+ managé](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)