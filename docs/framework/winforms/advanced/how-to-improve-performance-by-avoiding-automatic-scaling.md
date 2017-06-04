---
title: "Comment&#160;: am&#233;liorer les performances en &#233;vitant la mise &#224; l&#39;&#233;chelle automatique | Microsoft Docs"
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
  - "mise à l'échelle automatique"
  - "images (Windows Forms), améliorer les performances"
  - "images (Windows Forms), utiliser sans la mise à l'échelle automatique"
  - "performances, améliorer l'image"
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: am&#233;liorer les performances en &#233;vitant la mise &#224; l&#39;&#233;chelle automatique
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut automatiquement mettre à l'échelle une image pendant que vous la dessinez, ce qui peut affecter les performances.  Par ailleurs, vous pouvez contrôler la mise à l'échelle de l'image en passant les dimensions du rectangle de destination à la méthode <xref:System.Drawing.Graphics.DrawImage%2A>.  
  
 Par exemple, l'appel suivant à la méthode <xref:System.Drawing.Graphics.DrawImage%2A> spécifie un coin supérieur gauche de \(50, 30\), mais ne spécifie pas de rectangle de destination.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 Bien qu'il s'agisse de la version la plus simple de la méthode <xref:System.Drawing.Graphics.DrawImage%2A> en termes de nombre d'arguments requis, elle n'est pas nécessairement la plus efficace.  Si la résolution utilisée par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] \(habituellement 96 points par pouce\) est différente de la résolution stockée dans l'objet <xref:System.Drawing.Image>, la méthode <xref:System.Drawing.Graphics.DrawImage%2A> mettra à l'échelle l'image.  Par exemple, supposons qu'un objet <xref:System.Drawing.Image> ait une largeur de 216 pixels et une valeur de résolution horizontale stockée de 72 points par pouce.  Comme 216\/72 est égal à 3, <xref:System.Drawing.Graphics.DrawImage%2A> dimensionnera l'image pour qu'elle ait une largeur de 3 pouces à une résolution de 96 points par pouce.  Autrement dit, <xref:System.Drawing.Graphics.DrawImage%2A> affichera une image d'une largeur de 96 x 3 \= 288 pixels.  
  
 Même si votre résolution d'écran n'est pas de 96 points par pouce, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] mettra probablement l'image à l'échelle comme si la résolution d'écran était de 96 points par pouce.  Ceci est dû au fait qu'un objet [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<xref:System.Drawing.Graphics> est associé à un contexte de périphérique, par conséquent, lorsque [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] interroge le contexte de périphérique pour la résolution d'écran, le résultat est habituellement 96, quelle que soit la résolution d'écran réelle.  Vous pouvez éviter la mise à l'échelle automatique en spécifiant le rectangle de destination dans la méthode <xref:System.Drawing.Graphics.DrawImage%2A>.  
  
## Exemple  
 L'exemple suivant dessine deux fois la même image.  Dans le premier cas, la largeur et la hauteur du rectangle de destination ne sont pas spécifiées et l'image est automatiquement dimensionnée.  Dans le deuxième cas, la largeur et la hauteur \(mesurées en pixels\) du rectangle de destination sont spécifiées comme étant les mêmes que la largeur et la hauteur de l'image d'origine.  L'illustration suivante montre l'image rendue deux fois.  
  
 ![Texture mise à l'échelle](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  Remplacez Texture.jpg par le nom et le chemin d'accès d'une image valides sur votre système.  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)