---
title: "Splines cardinales dans GDI+ | Microsoft Docs"
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
  - "splines cardinales"
  - "GDI+, splines cardinales"
  - "splines, cardinales"
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Splines cardinales dans GDI+
Une spline cardinale est une séquence de courbes reliées entre elles pour former une courbe plus grande.  La spline est spécifiée par un tableau de points et un paramètre de tension.  Une spline cardinale passe par tous les points du tableau sans former d'angles et sans créer de brusques changements de tension de la courbe.  L'illustration suivante représente un ensemble de points et une spline cardinale qui passe par tous ces points.  
  
 ![Spline cardinale](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.png "Aboutgdip02\_art09")  
  
## Splines physiques et mathématiques  
 Dans le domaine industriel, une spline \(appelée fausse languette\) est une petite pièce de bois \(ou autre matériau flexible\).  Avant l'introduction des splines mathématiques, les dessinateurs industriels utilisaient des fausses languettes pour dessiner des courbes.  Ils plaçaient la fausse languette sur une feuille de papier et la fixaient en divers points prédéfinis.  Il suffisait ensuite de suivre le bord de la fausse languette avec un stylo ou un crayon pour dessiner la courbe.  Un même ensemble de points pouvait produire des courbes différentes en fonction des propriétés de la fausse languette.  Par exemple, une fausse languette présentant une forte résistance à la flexion ne donnait pas la même courbe qu'une fausse languette très souple.  
  
 En mathématiques, les formules utilisées pour les splines sont basées sur les propriétés de baguettes flexibles ; elles produisent donc des courbes analogues à celles que l'on obtenait avec des fausses languettes.  À partir d'un même ensemble de points, des fausses languettes de flexibilité différente produisaient des courbes différentes ; de même, les splines mathématiques définies avec le même ensemble de points mais des paramètres de tension différents donnent des courbes différentes.  L'illustration suivante représente quatre splines cardinales passant par le même ensemble de points.  La tension est indiquée pour chaque spline.  La valeur 0 correspond à une tension physique infinie qui force la courbe à prendre le chemin le plus court \(ligne droite\) entre les points.  La valeur 1 correspond à une tension physique nulle qui permet de relier les points par un tracé de courbure minimum.  Avec des valeurs de tension supérieures à 1, la courbe se comporte comme un ressort qui se détend pour prendre le chemin le plus long entre les points.  
  
 ![Splines cardinales](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.png "Aboutgdip02\_art10")  
  
 Les quatre splines de l'illustration précédente partagent la même tangente au point de départ.  La tangente est une ligne qui va du point de départ au point suivant de la courbe.  De même, la tangente commune en fin de courbe est une ligne qui va du dernier à l'avant\-dernier point de la courbe.  
  
 Pour dessiner une spline cardinale, il vous faut une instance de la classe <xref:System.Drawing.Graphics>, un objet <xref:System.Drawing.Pen> et un tableau d'objets <xref:System.Drawing.Point>. L'instance de la classe <xref:System.Drawing.Graphics> fournit la méthode <xref:System.Drawing.Graphics.DrawCurve%2A> qui dessine la spline et l'objet <xref:System.Drawing.Pen> stocke les attributs de la spline, notamment la largeur et la couleur de la ligne.  Le tableau d'objets <xref:System.Drawing.Point> stocke les points par lesquels la courbe doit passer.  L'exemple de code suivant montre comment dessiner une spline cardinale qui passe par les points définis dans  `myPointArray`.  Le troisième paramètre indique la tension.  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## Voir aussi  
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Génération et dessin de courbes](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)