---
title: "G&#233;n&#233;ration et dessin de courbes | Microsoft Docs"
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
  - "courbes, dessiner"
  - "dessiner, courbes"
  - "exemples (Windows Forms), dessiner des courbes"
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# G&#233;n&#233;ration et dessin de courbes
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] prend en charge plusieurs types de courbes : ellipses, arcs, splines cardinales et splines de Bézier.  Une ellipse se définit d'après son rectangle englobant ; un arc est une partie d'ellipse définie par un angle de début et un angle de balayage.  Une spline cardinale est définie par une matrice de points et un paramètre de tension. La courbe passe avec souplesse par chaque point de la matrice et le paramètre de tension influence la forme donnée à la courbe.  Une spline de Bézier se définit par deux points d'extrémité et deux points de contrôle. La courbe ne passe pas par ces points de contrôle qui influencent cependant la direction et la forme de la courbe lorsque celle\-ci passe d'un point de terminaison à l'autre.  
  
## Dans cette section  
 [Comment : dessiner des splines cardinales](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 Décrit des splines cardinales et explique comment les dessiner.  
  
 [Comment : dessiner une spline de Bézier unique](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 Décrit une spline de Bézier et indique comment en dessiner une.  
  
 [Comment : dessiner une séquence de splines de Bézier](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 Explique comment dessiner plusieurs splines de Bézier dans l'ordre.