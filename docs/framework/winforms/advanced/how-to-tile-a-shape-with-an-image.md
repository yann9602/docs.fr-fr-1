---
title: "Comment&#160;: remplir une forme avec une image | Microsoft Docs"
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
  - "bitmaps (Windows Forms), remplir les formes avec"
  - "images (Windows Forms), remplir les formes avec"
  - "formes, mettre en mosaïque avec les images"
  - "pinceaux de texture, mettre les images en mosaïque avec"
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: remplir une forme avec une image
À l'instar de carreaux d'un sol carrelé, des images rectangulaires peuvent être placées côte à côte pour remplir une forme \(en mosaïque\).  Pour remplir avec une mosaïque l'intérieur d'une forme, utilisez une brosse texturée.  Lorsque vous construisez un objet <xref:System.Drawing.TextureBrush>, l'un des arguments que vous passez au constructeur est un objet <xref:System.Drawing.Image>.  Lorsque vous utilisez la brosse texturée pour peindre l'intérieur d'une forme, la forme est remplie par des copies répétées de cette image.  
  
 La propriété WrapMode \(mode habillage\) de l'objet <xref:System.Drawing.TextureBrush> détermine l'orientation de l'image lors de sa répétition dans une grille rectangulaire.  Toutes les images de la mosaïque dans la grille peuvent avoir la même orientation, ou vous pouvez prévoir une rotation d'une position d'image à la suivante.  La rotation peut être horizontale, verticale ou les deux.  Les exemples suivants illustrent une mosaïque avec différents types de rotation.  
  
### Pour disposer une image en mosaïque  
  
-   Cet exemple utilise l'image 75×75 suivante pour disposer un rectangle 200×200 en mosaïque.  
  
 ![Mosaïque 1](../../../../docs/framework/winforms/advanced/media/tile1.png "tile1")  
  
-   L'illustration suivante montre comment la mosaïque de l'image remplit le rectangle.  Notez que toutes les images de la mosaïque ont la même orientation, sans rotation.  
  
 ![Mosaïque 2](../../../../docs/framework/winforms/advanced/media/tile2.png "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### Pour faire pivoter une image horizontalement lors de la disposition en mosaïque  
  
-   Cet exemple utilise la même image 75×75 pour remplir un rectangle 200×200.  Le mode habillage prévoit une rotation horizontale de l'image.  L'illustration suivante montre comment la mosaïque de l'image remplit le rectangle.  Notez que, lors du passage d'une image à la suivante dans une ligne donnée, l'image effectue une rotation horizontale.  
  
 ![Mosaïque 3](../../../../docs/framework/winforms/advanced/media/tile3.png "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### Pour faire pivoter une image verticalement lors de la disposition en mosaïque  
  
-   Cet exemple utilise la même image 75×75 pour remplir un rectangle 200×200.  Le mode habillage prévoit une rotation verticale de l'image.  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### Pour faire pivoter une image horizontalement et verticalement lors de la disposition en mosaïque  
  
-   Cet exemple utilise la même image 75×75 pour disposer un rectangle 200×200 en mosaïque.  Le mode habillage prévoit des rotations horizontale et verticale de l'image.  L'illustration suivante montre comment la mosaïque de l'image remplit le rectangle.  Notez que, lors du passage d'une image à la suivante dans une ligne donnée, l'image effectue une rotation horizontale, et lorsque vous passez d'une image à la suivante dans une colonne donnée, l'image effectue une rotation verticale.  
  
 ![Mosaïque 5](../../../../docs/framework/winforms/advanced/media/tile5.png "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## Voir aussi  
 [Utilisation d'un pinceau pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)