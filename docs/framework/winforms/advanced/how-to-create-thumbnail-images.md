---
title: "Comment : créer des images miniatures"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a3866274340932819a419c622c10072dd67c439
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-thumbnail-images"></a>Comment : créer des images miniatures
Une image miniature est une version réduite d’une image. Vous pouvez créer une image miniature en appelant le <xref:System.Drawing.Image.GetThumbnailImage%2A> méthode d’un <xref:System.Drawing.Image> objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant construit une <xref:System.Drawing.Image> objet à partir d’un fichier JPG. L’image d’origine a une largeur de 640 pixels et une hauteur de 479 pixels. Le code crée une image miniature qui a une largeur de 100 pixels et une hauteur de 100 pixels.  
  
 L’illustration suivante montre l’image miniature.  
  
 ![Image miniature](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  Dans cet exemple, une méthode de rappel est déclarée, mais jamais utilisée. Il prend en charge toutes les versions de GDI +.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>. Pour exécuter l’exemple, procédez comme suit :  
  
1.  Créez une application Windows Forms.  
  
2.  Ajoutez l’exemple de code au formulaire.  
  
3.  Créer un gestionnaire pour du formulaire <xref:System.Windows.Forms.Control.Paint> événement  
  
4.  Dans le <xref:System.Windows.Forms.Control.Paint> gestionnaire, appelez le `GetThumbnail` méthode et passe `e` pour <xref:System.Windows.Forms.PaintEventArgs>.  
  
5.  Rechercher un fichier image que vous souhaitez faire une miniature.  
  
6.  Dans le `GetThumbnail` (méthode), spécifiez le chemin d’accès et le nom de votre image.  
  
7.  Appuyez sur F5 pour exécuter l’exemple.  
  
     Une image miniature 100 par 100 s’affiche sur le formulaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
