---
title: "Comment&#160;: charger et afficher des m&#233;tafichiers | Microsoft Docs"
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
  - "exemples (Windows Forms), métafichiers"
  - "métafichiers, afficher"
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: charger et afficher des m&#233;tafichiers
La classe <xref:System.Drawing.Imaging.Metafile>, qui hérite de la classe <xref:System.Drawing.Image>, fournit des méthodes pour l'enregistrement, l'affichage et l'examen d'images vectorielles.  
  
## Exemple  
 Pour afficher une image vectorielle \(métafichier\) à l'écran, vous avez besoin d'un objet <xref:System.Drawing.Imaging.Metafile> et d'un objet <xref:System.Drawing.Graphics>.  Passez le nom d'un fichier \(ou d'un flux\) à un constructeur <xref:System.Drawing.Imaging.Metafile>.  Après avoir créé un objet <xref:System.Drawing.Imaging.Metafile>, passez cet objet <xref:System.Drawing.Imaging.Metafile> à la méthode <xref:System.Drawing.Graphics.DrawImage%2A> d'un objet <xref:System.Drawing.Graphics>.  
  
 L'exemple crée un objet <xref:System.Drawing.Imaging.Metafile> à partir d'un fichier EMF \(métafichier amélioré\) et dessine l'image en positionnant son coin supérieur gauche à \(60, 10\).  
  
 L'illustration suivante montre le métafichier dessiné à l'emplacement spécifié.  
  
 ![Position de l'image](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)