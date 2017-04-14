---
title: "Utilisation d&#39;un pinceau &#224; d&#233;grad&#233; pour remplir des formes | Microsoft Docs"
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
  - "pinceaux, pinceaux à couleurs dégradées"
  - "exemples (Windows Forms), pinceaux à couleurs dégradées"
  - "pinceaux à couleurs dégradées"
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Utilisation d&#39;un pinceau &#224; d&#233;grad&#233; pour remplir des formes
Un pinceau à dégradé permet de remplir une forme avec une couleur qui se modifie progressivement.  Vous pouvez ainsi employer un dégradé horizontal pour remplir une forme de telle sorte que la couleur changera progressivement tandis que vous vous déplacerez du bord gauche de la forme vers son bord droit.  Imaginez un rectangle ayant un bord gauche de couleur noire \(représenté par les composantes rouge, vert et bleu 0,0,0\) et un bord droit de couleur rouge \(représenté par 255, 0, 0\).  Si la longueur du rectangle correspond à 256 pixels, la composante rouge d'un pixel donné sera supérieure à la composante rouge du pixel situé à sa gauche.  Le pixel à l'extrémité gauche d'une ligne a pour composantes couleur \(0, 0, 0\), le deuxième pixel a \(1, 0, 0\), le troisième \(2, 0, 0\) et ainsi de suite jusqu'à ce que vous parveniez au pixel le plus à droite dont les composantes couleur sont \(255, 0, 0\).  L'interpolation de ces valeurs de couleur constitue le dégradé de couleur.  
  
 Un dégradé linéaire fait varier la couleur tandis que vous vous déplacez horizontalement, verticalement ou parallèlement à un trait oblique spécifié.  Un dégradé de tracé fait varier la couleur tandis que vous vous déplacez à l'intérieur et sur le contour d'un tracé.  Vous pouvez personnaliser les dégradés de tracé pour créer une multitude d'effets.  
  
 L'illustration suivante montre un rectangle rempli au moyen d'un pinceau à dégradé linéaire et une ellipse remplie avec un pinceau à dégradé 2D.  
  
 ![Dégradé](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## Dans cette section  
 [Comment : créer un dégradé linéaire](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 Indique comment créer un dégradé linéaire à l'aide de la classe <xref:System.Drawing.Drawing2D.LinearGradientBrush>.  
  
 [Comment : créer un dégradé de tracé](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 Décrit comment créer un dégradé de tracé à l'aide de la classe <xref:System.Drawing.Drawing2D.PathGradientBrush>.  
  
 [Comment : appliquer une correction gamma à un dégradé](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 Explique comment utiliser la correction gamma avec un pinceau à dégradé.  
  
## Référence  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=fullName>  
 Contient une description de cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=fullName>  
 Contient une description de cette classe et propose des liens vers tous ses membres.