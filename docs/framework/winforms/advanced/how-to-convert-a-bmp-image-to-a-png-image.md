---
title: "Comment&#160;: convertir une image&#160;BMP en image&#160;PNG | Microsoft Docs"
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
  - "BMP (images), convertir en PNG"
  - "formats des images, convertir entre"
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: convertir une image&#160;BMP en image&#160;PNG
Il peut arriver que vous souhaitiez effectuer une conversion d'un format de fichier image vers un autre.  Vous pouvez facilement effectuer cette conversion en appelant la méthode <xref:System.Drawing.Image.Save%2A> de la classe <xref:System.Drawing.Image> et en spécifiant le <xref:System.Drawing.Imaging.ImageFormat> pour le format de fichier image souhaité.  
  
## Exemple  
 L'exemple suivant charge une image BMP à partir d'un type et enregistre l'image au format PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   une application Windows Forms ;  
  
-   une référence à l'espace de noms `System.Drawing.Imaging`.  
  
## Voir aussi  
 [Comment : répertorier les encodeurs installés](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)   
 [Utilisation d'encodeurs et de décodeurs d'images dans GDI\+ managé](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)   
 [Types de bitmaps](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)