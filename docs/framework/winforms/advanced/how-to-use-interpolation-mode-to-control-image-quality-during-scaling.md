---
title: "Comment&#160;: utiliser le mode d&#39;interpolation pour contr&#244;ler la qualit&#233; d&#39;image pendant la mise &#224; l&#39;&#233;chelle | Microsoft Docs"
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
  - "images (Windows Forms), contrôler la qualité"
  - "images (Windows Forms), mettre à l'échelle"
  - "mode d'interpolation, contrôler la qualité des images"
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: utiliser le mode d&#39;interpolation pour contr&#244;ler la qualit&#233; d&#39;image pendant la mise &#224; l&#39;&#233;chelle
Le mode d'interpolation d'un objet <xref:System.Drawing.Graphics> influence la façon dont [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] met à l'échelle \(étire et réduit\) les images.  L'énumération <xref:System.Drawing.Drawing2D.InterpolationMode> définit plusieurs modes d'interpolation, dont certains sont répertoriés dans la liste suivante :  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
 Pour étirer une image, chaque pixel de l'image d'origine doit être mappé à un groupe de pixels de l'image plus grande.  Pour réduire une image, des groupes de pixels dans l'image d'origine doivent être mappés à des pixels individuels dans l'image plus petite.  L'efficacité des algorithmes qui effectuent ces mappages détermine la qualité d'une image dimensionnée.  Les algorithmes qui produisent des images dimensionnées de qualité supérieure ont tendance à nécessiter plus de temps de traitement.  Dans la liste précédente, le mode <xref:System.Drawing.Drawing2D.InterpolationMode> présente la moins bonne qualité, le mode <xref:System.Drawing.Drawing2D.InterpolationMode> la meilleure.  
  
 Pour définir le mode d'interpolation, assignez un des membres de l'énumération <xref:System.Drawing.Drawing2D.InterpolationMode> à la propriété <xref:System.Drawing.Graphics.InterpolationMode%2A> d'un objet <xref:System.Drawing.Graphics>.  
  
## Exemple  
 L'exemple suivant dessine une image, puis réduit l'image avec trois modes d'interpolation différents :  
  
 L'illustration suivante montre l'image d'origine et les trois images plus petites.  
  
 ![Image avec paramètres d'interpolation variés](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [Utilisation des images, bitmaps, icônes et métafichiers](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)