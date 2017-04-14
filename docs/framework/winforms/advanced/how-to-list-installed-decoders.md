---
title: "Comment&#160;: r&#233;pertorier les d&#233;codeurs install&#233;s | Microsoft Docs"
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
  - "décodeurs d'image, répertorier"
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: r&#233;pertorier les d&#233;codeurs install&#233;s
Vous pouvez répertorier les décodeurs d'images disponibles sur un ordinateur afin de déterminer si votre application peut lire un format de fichier d'image spécifique.  La classe <xref:System.Drawing.Imaging.ImageCodecInfo> fournit les méthodes statiques <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> permettant de déterminer les décodeurs d'image disponibles.  <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> retourne un tableau d'objets <xref:System.Drawing.Imaging.ImageCodecInfo>.  
  
## Exemple  
 L'exemple de code suivant présente la liste des décodeurs installés et leurs valeurs de propriété.  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Une application Windows Forms.  
  
-   <xref:System.Windows.Forms.PaintEventArgs>, un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Comment : répertorier les encodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)   
 [Utilisation d'encodeurs et de décodeurs d'images dans GDI\+ managé](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)