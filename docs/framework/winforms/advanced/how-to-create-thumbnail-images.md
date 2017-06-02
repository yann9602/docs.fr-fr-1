---
title: "Comment&#160;: cr&#233;er des images miniatures | Microsoft Docs"
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
  - "images (Windows Forms), créer des miniatures"
  - "images miniatures, créer"
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Comment&#160;: cr&#233;er des images miniatures
Une image miniature est une petite version d'une image.  Vous pouvez créer une image miniature en appelant la méthode <xref:System.Drawing.Image.GetThumbnailImage%2A> d'un objet <xref:System.Drawing.Image>.  
  
## Exemple  
 L'exemple suivant montre comment construire un objet <xref:System.Drawing.Image> à partir d'un fichier JPEG.  L'image d'origine a une largeur de 640 pixels et une hauteur de 479 pixels.  Le code crée une image miniature d'une largeur de 100 pixels et d'une hauteur de 100 pixels.  
  
 L'illustration suivante montre l'image miniature.  
  
 ![Image miniature](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  Dans cet exemple, une méthode de rappel est déclarée, mais elle n'est jamais utilisée.  Toutes les versions de GDI\+ sont prises en charge.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Pour exécuter l'exemple, suivez ces étapes :  
  
1.  Créer une nouvelle application Windows Forms.  
  
2.  Ajoutez l'exemple de code au formulaire.  
  
3.  Créez un gestionnaire pour l'événement <xref:System.Windows.Forms.Control.Paint> de ce formulaire.  
  
4.  Dans le gestionnaire <xref:System.Windows.Forms.Control.Paint>, appelez la méthode `GetThumbnail` et passez `e` pour <xref:System.Windows.Forms.PaintEventArgs>.  
  
5.  Recherchez un fichier image dont vous souhaitez faire une miniature.  
  
6.  Dans la méthode `GetThumbnail`, spécifiez le chemin d'accès et le nom de fichier de votre image.  
  
7.  Appuyez sur F5 pour exécuter l'exemple.  
  
     Une image miniature 100 par 100 s'affiche sur le formulaire.  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)