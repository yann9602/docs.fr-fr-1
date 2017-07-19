---
title: "Comment&#160;: appliquer une correction gamma &#224; un d&#233;grad&#233; | Microsoft Docs"
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
  - "pinceaux à couleurs dégradées, correction gamma"
  - "dégradés, correction gamma"
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: appliquer une correction gamma &#224; un d&#233;grad&#233;
Vous pouvez activer la correction gamma pour un pinceau à dégradé linéaire en affectant à la propriété <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> du pinceau la valeur `true`.  Vous pouvez désactiver la correction gamma en affectant à cette même propriété la valeur `false`.  Ce type de correction est désactivé par défaut.  
  
## Exemple  
 L'exemple crée un pinceau à dégradé linéaire et l'utilise pour remplir deux rectangles.  Le premier est rempli sans correction gamma, tandis que le second est rempli avec cette correction.  
  
 L'illustration suivante présente les deux rectangles remplis.  Celui du haut, sans la correction gamma, est foncé en son milieu.  Celui du bas, avec la correction gamma, présente une intensité plus régulière.  
  
 ![Dégradé](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>   
 [Utilisation d'un pinceau à dégradé pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)