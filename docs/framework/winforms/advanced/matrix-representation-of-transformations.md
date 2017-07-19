---
title: "Repr&#233;sentation matricielle des transformations | Microsoft Docs"
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
  - "transformations affines"
  - "transformations composites"
  - "transformations linéaires"
  - "matrices"
  - "transformations, composites"
  - "transformations, linéaires"
  - "transformations, représentation matricielle de"
  - "transformations, translation"
  - "translations dans une représentation matricielle"
  - "vecteurs"
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Repr&#233;sentation matricielle des transformations
Une matrice m×n est un ensemble de nombres organisés en m lignes et n colonnes.  L'illustration suivante représente plusieurs matrices.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.png "AboutGdip05\_art04")  
  
 Vous pouvez additionner deux matrices de même taille en additionnant leurs éléments.  L'illustration suivante montre deux exemples d'addition de matrices.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.png "AboutGdip05\_art05")  
  
 Vous pouvez multiplier une matrice m×n par une matrice n×p ; le résultat sera une matrice m×p.  Le nombre de colonnes de la première matrice doit être égal au nombre de lignes de la seconde matrice.  Par exemple, si vous multipliez une matrice 4×2 par une matrice 2×3, vous obtiendrez une matrice 4×3.  
  
 Vous pouvez considérer les points dans le plan et les lignes et colonnes d'une matrice comme des vecteurs.  Par exemple, \(2, 5\) est un vecteur à deux composants et \(3, 7, 1\) est un vecteur à trois composants.  Le produit scalaire de deux vecteurs est défini comme suit :  
  
 \(a, b\) • \(c, d\) \= ac \+ bd  
  
 \(a, b, c\) • \(d, e, f\) \= ad \+ be \+ cf  
  
 Par exemple, le produit scalaire de \(2, 3\) et \(5, 4\) est \(2\)\(5\) \+ \(3\)\(4\) \= 22.  Le produit scalaire de \(2, 5, 1\) et \(4, 3, 1\) est \(2\)\(4\) \+ \(5\)\(3\) \+ \(1\)\(1\) \= 24.  Notez que le produit scalaire de deux vecteurs est un nombre et non un autre vecteur.  En outre, vous ne pouvez calculer le produit scalaire de deux vecteurs que s'ils ont le même nombre de composants.  
  
 Soit A\(i, j\) l'entrée de la matrice A située dans la ligne i et la colonne j.  Par exemple, A\(3, 2\) est l'entrée située dans la troisième ligne et la deuxième colonne de la matrice A.  Supposez les matrices A, B et C et AB \= C.  Les entrées de C sont calculées comme suit :  
  
 C\(i, j\) \= \(ligne i de A\) • \(colonne j de B\)  
  
 L'illustration suivante montre plusieurs exemples de multiplication de matrices.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.png "AboutGdip05\_art06")  
  
 Si vous considérez qu'un point dans un plan est une matrice 1×2, vous pouvez transformer ce point en le multipliant par une matrice 2×2.  L'illustration suivante représente plusieurs transformations appliquées au point \(2, 1\).  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05\_art07")  
  
 Toutes les transformations illustrées dans la figure précédente sont des transformations linéaires.  Certaines transformations \(notamment la translation\) ne sont pas linéaires et ne peuvent pas s'exprimer sous la forme d'une multiplication par une matrice 2×2.  Supposons que vous partez du point \(2, 1\) et lui appliquez successivement une rotation à 90 degrés, une translation de 3 unités dans la direction x et une translation de 4 unités dans la direction y.  Vous pouvez utiliser une multiplication de matrices suivie d'une addition de matrices.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05\_art08")  
  
 Une transformation linéaire \(multiplication par une matrice 2×2\) suivie d'une translation \(addition d'une matrice 1×2\) est appelée une transformation affine.  Au lieu d'utiliser une paire de matrices \(une pour la transformation linéaire et une autre pour la translation\), vous pouvez stocker l'ensemble d'une transformation affine dans une matrice 3×3.  Pour ce faire, il faut stocker un point du plan sous la forme d'une matrice 1×3 avec une troisième coordonnée factice.  La technique habituelle consiste à rendre toutes les 3e coordonnées égales à 1.  Par exemple, le point \(2, 1\) est représenté par la matrice \[2 1 1\].  L'illustration suivante montre une transformation affine \(rotation à 90 degrés, translation de 3 unités dans la direction x et de 4 unités dans la direction y\) exprimée sous la forme d'une multiplication par une seule matrice 3×3.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.png "AboutGdip05\_art09")  
  
 Dans l'exemple précédent, le point \(2, 1\) est mappé au point \(2, 6\).  Notez que la troisième colonne de la matrice 3×3 contient les nombres 0, 0, 1.  Ce sera toujours le cas pour la matrice 3×3 d'une transformation affine.  Les nombres importants sont les six nombres des colonnes 1 et 2.  La partie supérieure gauche 2×2 de la matrice représente la partie linéaire de la transformation alors que les deux premières entrées de la 3e ligne représentent la translation.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05\_art10")  
  
 Dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], les transformations affines peuvent être stockées dans un objet <xref:System.Drawing.Drawing2D.Matrix>.  Comme la troisième colonne d'une matrice représentant une transformation affine contient toujours \(0, 0, 1\), vous spécifiez uniquement les six nombres des deux premières colonnes lorsque vous construisez un objet <xref:System.Drawing.Drawing2D.Matrix>.  L'instruction `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` construit la matrice illustrée par la figure précédente.  
  
## Transformations composites  
 Une transformation composite est une séquence de transformations successives.  Prenons les matrices et les transformations suivantes :  
  
|||  
|-|-|  
|Matrice A|Rotation de 90 degrés|  
|Matrice B|Mise à l'échelle par un facteur 2 dans la direction x|  
|Matrice C|Translation de 3 unités dans la direction y|  
  
 En multipliant le point de départ \(2, 1\) — représenté par la matrice \[2 1 1\] — successivement par A, B et C, vous lui appliquez les trois transformations dans l'ordre indiqué ci\-dessus.  
  
 \[2 1 1\]ABC \= \[\-2 5 1\]  
  
 Au lieu d'utiliser trois matrices distinctes, vous pouvez multiplier les matrices A, B et C entre elles pour obtenir une matrice 3×3 unique qui stocke l'ensemble de la transformation composite.  Supposez ABC \= D.  Puis, un point multiplié par D qui donne le même résultat qu'un point multiplié par A, puis B, puis C.  
  
 \[2 1 1\]D \= \[\-2 5 1\]  
  
 L'illustration suivante représente les matrices A, B, C et D.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.png "AboutGdip05\_art12")  
  
 S'il est possible de former la matrice d'une transformation composite en multipliant entre elles les matrices de transformation individuelles, il est possible de stocker dans un objet <xref:System.Drawing.Drawing2D.Matrix> unique une séquence quelconque de transformations affines.  
  
> [!CAUTION]
>  L'ordre est important dans une transformation composite.  En général, la séquence rotation\-mise à l'échelle\-translation n'est pas équivalente à la séquence mise à l'échelle\-rotation\-translation.  De même, l'ordre de multiplication des matrices est important.  En général, ABC n'est pas identique à BAC.  
  
 La classe <xref:System.Drawing.Drawing2D.Matrix> fournit plusieurs méthodes pour créer une transformation composite : <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A> et <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>.  L'exemple suivant crée la matrice d'une transformation composite qui effectue tout d'abord une rotation à 30 degrés, puis une mise à l'échelle par un facteur 2 dans la direction y et enfin une translation de 5 unités dans la direction x :  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 L'illustration suivante représente cette matrice.  
  
 ![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.png "AboutGdip05\_art13")  
  
## Voir aussi  
 [Systèmes de coordonnées et transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [Utilisation des transformations dans GDI\+ managé](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)