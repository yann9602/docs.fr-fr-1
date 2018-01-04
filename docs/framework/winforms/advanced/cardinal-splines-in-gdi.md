---
title: Splines cardinales dans GDI+
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
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b7653e05fff241f05836624ff02273fb8c24ef6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cardinal-splines-in-gdi"></a>Splines cardinales dans GDI+
Une spline cardinale est une séquence de courbes reliées entre elles pour former une courbe plus grande. La spline est spécifiée par un tableau de points et un paramètre de tension. Une spline cardinale passe correctement sur chaque point dans le tableau ; Il existe des angles aigus et aucune modification brusque dans la précision de la courbe. L’illustration suivante montre un ensemble de points et une spline cardinale qui passe par chaque point dans le jeu.  
  
 ![Spline cardinale](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>Splines physiques et mathématiques  
 Une spline physique est un élément dynamique de bois ou autre matériau flexible. Avant l’arrivée des splines mathématiques, les concepteurs utilisés splines physiques pour dessiner des courbes. Un concepteur est placer la spline sur une feuille de papier et ancrez-la à un ensemble donné de points. Le concepteur peut ensuite créer une courbe en dessinant le long de la spline avec un stylet ou un crayon. Un ensemble donné de points peut produire des courbes, en fonction des propriétés de la spline physique différentes. Par exemple, une spline avec une forte résistance à pliage produirait une courbe différente à une spline extrêmement flexible.  
  
 Les formules de splines mathématiques sont basées sur les propriétés de profilés flexibles, afin des courbes produites par des splines mathématiques sont similaires aux courbes qui ont été générés une fois par splines physiques. Comme splines physiques de différents tension produira différentes courbes via un ensemble donné de points, des splines mathématiques avec des valeurs différentes pour le paramètre de tension produira différentes courbes via un ensemble donné de points. L’illustration suivante montre quatre splines cardinales passant par le même ensemble de points. La tension est indiquée pour chaque spline. La valeur 0 correspond à une tension physique infinie qui force la courbe à prendre le plus court (ligne droite) entre les points. La valeur 1 correspond à aucune tension physique, ce qui permet la spline prendre le chemin d’accès de courbure minimum. Avec les valeurs de tension supérieures à 1, la courbe se comporte comme un ressort, envoyée à prendre le chemin le plus long.  
  
 ![Splines cardinales](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 Les quatre splines de l’illustration précédente partagent la même tangente au point de départ. La tangente est la ligne dessinée à partir du point de départ au point suivant le long de la courbe. De même, la tangente partagée sur le point de fin est la ligne tracée à partir du point de fin au point précédent sur la courbe.  
  
 Pour dessiner une spline cardinale, vous avez besoin d’une instance de la <xref:System.Drawing.Graphics> (classe), un <xref:System.Drawing.Pen>et un tableau de <xref:System.Drawing.Point> objets de l’instance de la <xref:System.Drawing.Graphics> classe fournit le <xref:System.Drawing.Graphics.DrawCurve%2A> méthode, qui dessine la spline, et le <xref:System.Drawing.Pen> stocke les attributs de la spline, telles que la largeur de ligne et la couleur. Le tableau de <xref:System.Drawing.Point> objets stocke les points de la courbe doit passer. L’exemple de code suivant montre comment dessiner une spline cardinale qui passe par les points dans `myPointArray`. Le troisième paramètre est la tension.  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Voir aussi  
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Génération et dessin de courbes](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
