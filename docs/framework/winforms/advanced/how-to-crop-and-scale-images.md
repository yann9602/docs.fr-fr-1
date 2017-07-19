---
title: "Comment&#160;: rogner et mettre &#224; l&#39;&#233;chelle des images | Microsoft Docs"
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
  - "images (Windows Forms), rogner"
  - "images (Windows Forms), mettre à l'échelle"
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: rogner et mettre &#224; l&#39;&#233;chelle des images
La classe <xref:System.Drawing.Graphics> fournit plusieurs méthodes <xref:System.Drawing.Graphics.DrawImage%2A>, dont certaines ont des paramètres de rectangle source et destination que vous pouvez utiliser pour rogner et mettre à l'échelle des images.  
  
## Exemple  
 L'exemple suivant montre comment construire un objet <xref:System.Drawing.Image> à partir du fichier sur disque Apple.gif.  Le code dessine l'image d'une pomme entière, à sa taille d'origine.  Le code appelle ensuite la méthode <xref:System.Drawing.Graphics.DrawImage%2A> d'un objet <xref:System.Drawing.Graphics> pour dessiner une partie de l'image de la pomme dans un rectangle de destination plus grand que l'image d'origine.  
  
 La méthode <xref:System.Drawing.Graphics.DrawImage%2A> détermine la partie de la pomme à dessiner en examinant le rectangle source, qui est spécifié par les troisième, quatrième, cinquième et sixième arguments.  Dans ce cas, la pomme est rognée à 75 pour cent de sa largeur et 75 pour cent de sa hauteur.  
  
 La méthode <xref:System.Drawing.Graphics.DrawImage%2A> détermine l'emplacement où dessiner la pomme rognée et la taille à attribuer à la pomme rognée en examinant le rectangle de destination qui est spécifié par le deuxième argument.  Dans ce cas, le rectangle de destination est 30 pour cent plus large et 30 pour cent plus haut que l'image d'origine.  
  
 L'illustration suivante montre la pomme d'origine et la pomme rognée mise à l'échelle.  
  
 ![Rogner et mettre à l'échelle](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Veillez à remplacer `Apple.gif` par le nom et le chemin d'accès d'un fichier image valides sur votre système.  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)