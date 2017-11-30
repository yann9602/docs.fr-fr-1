---
title: "Introduction aux contrôles Line et Shape (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e691d57c6de640c83556937eeddedf89e79b6846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Introduction aux contrôles Line et Shape (Visual Studio)
Les contrôles Visual Basic Power Packs Line et Shape sont un ensemble de trois contrôles graphiques qui vous permettent de dessiner des lignes et des formes sur des formulaires et des conteneurs. Le <xref:Microsoft.VisualBasic.PowerPacks.LineShape> contrôle est utilisé pour dessiner des lignes horizontales, verticales et diagonales. Le <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> contrôle est utilisé pour dessiner des cercles et des ovales et le <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> contrôle est utilisé pour dessiner des rectangles et des carrés.  
  
## <a name="line-and-shape-controls"></a>Contrôles Line et Shape  
 Contrôles Line et Shape encapsulent une bonne partie des méthodes graphiques qui sont contenus dans le <xref:System.Drawing> espace de noms. Cela vous permet de dessiner des lignes et des formes en une seule étape sans avoir à créer des pinceaux, des stylets et des objets graphiques. Des techniques telles que des dégradés graphiques complexes est possible en définissant quelques propriétés.  
  
 Bien qu’il est également possible de dessiner des lignes et des formes à l’aide de méthodes de graphiques, il existe plusieurs avantages à l’aide des contrôles Line et Shape :  
  
-   Les méthodes de graphiques peuvent être appelées uniquement au moment de l’exécution. Contrôles Line et Shape peuvent être ajoutés à un formulaire au moment du design. Cela vous permet de voir à quoi ils ressemblent et les positionner avec précision ; ils peuvent également être ajoutés au moment de l’exécution.  
  
-   Contrôles Line et Shape sont sélectionnables au moment de l’exécution, fournissant des événements tels que <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> et <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>. Les sorties des méthodes graphiques ne sont pas sélectionnables et ne fournissent pas d’événements.  
  
-   Les contrôles Line et Shape fournissent <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> et <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> les méthodes qui vous permettent de contrôler leur ordre de plan au moment du design et au moment de l’exécution. L’ordre de plan des méthodes graphiques peut être contrôlée uniquement en modifiant leur ordre d’exécution au moment de l’exécution.  
  
-   Contrôles Line et Shape sont des contrôles sans fenêtre ; ils n’ont aucun handle de fenêtre et par conséquent utilisent moins de ressources système.  
  
### <a name="object-model"></a>Modèle objet  
 Contrôles Line et Shape dérivent d’une base <xref:Microsoft.VisualBasic.PowerPacks.Shape> classe qui définit leurs propriétés partagées, les méthodes et les événements.  
  
 L’illustration suivante montre la hiérarchie des objets Line et Shape.  
  
 ![Un diagramme de la hiérarchie des objets Line et Shape](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Hiérarchie d’objets Line et Shape  
  
 Dérivé <xref:Microsoft.VisualBasic.PowerPacks.LineShape> classe contient des propriétés, méthodes et événements qui sont propres aux lignes. Dérivé <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> est la classe de base pour <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> et <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; il contient des propriétés, méthodes et événements communs à toutes les formes. Vous pouvez également dériver de <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> pour créer vos propres `Shape` contrôles.  
  
 Le <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> et <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> classes peuvent être utilisées pour dessiner des cercles, des ovales, des rectangles et des rectangles à angles arrondis.  
  
 Lorsqu’un contrôle Line ou Shape est ajouté à un formulaire ou un conteneur, un invisible <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> objet est créé. Le <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> agit comme une zone de dessin pour les formes au sein de chaque contrôle conteneur ; chaque <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> est associée à une <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> qui vous permet de parcourir les contrôles Line et Shape. Vous pouvez déplacer les formes d’un conteneur à un autre à l’aide des fonctions Couper et coller ou par glisser- déposer. Lorsque la dernière forme est supprimée d’un conteneur, le <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> est également supprimé.  
  
> [!NOTE]
>  Pas de tous les contrôles conteneur prend en charge les contrôles Line et Shape. Vous ne pouvez pas héberger un contrôle Line ou Shape sur un <xref:System.Windows.Forms.TableLayoutPanel> ou <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks>  
 [Guide pratique : dessiner des lignes avec le contrôle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Guide pratique : dessiner des formes avec les contrôles OvalShape et RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Guide pratique : activer la tabulation entre les formes](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
