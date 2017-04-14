---
title: "Fusion alpha de lignes et de remplissages | Microsoft Docs"
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
  - "fusion alpha"
  - "fusion alpha, utiliser avec les remplissages"
  - "fusion alpha, utiliser avec les lignes"
  - "exemples (Windows Forms), fusion alpha"
  - "remplissages, fusion alpha"
  - "lignes, ajouter de la transparence"
  - "lignes, fusion alpha"
  - "formes, ajouter de la transparence"
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Fusion alpha de lignes et de remplissages
Dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], une couleur est une valeur 32 bits avec 8 bits pour chaque valeur alpha, rouge, vert et bleu.  La valeur alpha indique la transparence de la couleur \(à quel point la couleur se fond à la couleur de l'arrière\-plan.  Les valeurs alpha sont comprises entre 0 et 255, où 0 représente une couleur entièrement transparente et 255 une couleur entièrement opaque.  
  
 La fusion alpha est un mélange pixel par pixel des données couleur de source et d'arrière\-plan.  Chacun des trois composants \(rouge, vert, bleu\) d'une source de couleur donnée se fond aux composants correspondants de la couleur d'arrière\-plan conformément à la formule suivante :  
  
 CouleurAffichage \= CouleurSource  × alpha \/ 255 \+ Couleur ArrièrePlan × \(255 – alpha\) \/ 255  
  
 Par exemple, supposez que le composant rouge de la couleur source soit de 150 et que le composant rouge de la couleur d'arrière\-plan soit de 100.  Si la valeur alpha est de 200, le composant rouge de la couleur résultante est calculé comme suit :  
  
 150 × 200 \/ 255 \+ 100 × \(255 – 200\) \/ 255 \= 139  
  
## Dans cette section  
 [Comment : dessiner des lignes opaques et translucides](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 Indique comment dessiner des lignes à contrôle alpha.  
  
 [Comment : dessiner avec des pinceaux opaques et translucides](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 Explique comment effectuer une opération de fusion à contrôle alpha avec des pinceaux.  
  
 [Comment : utiliser le mode de composition pour commander la fusion alpha](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 Décrit comment contrôler la fusion alpha à l'aide de <xref:System.Drawing.Drawing2D.CompositingMode>.  
  
 [Comment : utiliser une matrice de couleurs pour définir des valeurs alpha dans des images](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 Explique comment utiliser un objet <xref:System.Drawing.Imaging.ColorMatrix> pour effectuer une fusion alpha.