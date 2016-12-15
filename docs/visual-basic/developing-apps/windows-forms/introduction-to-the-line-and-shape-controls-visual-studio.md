---
title: "Introduction to the Line and Shape Controls (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Line control, overview"
  - "Shape control, overview"
  - "lines, drawing"
  - "shapes, drawing"
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Introduction to the Line and Shape Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les contrôles Line et Shape de Visual Basic Power Packs sont un jeu de trois contrôles graphiques qui vous permettent de dessiner des lignes et des formes sur des formulaires et des conteneurs.  Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.LineShape> est utilisé pour dessiner des lignes horizontales, verticales et diagonales.  Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> est utilisé pour dessiner des cercles et des ovales et le contrôle <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> pour dessiner des rectangles et des carrés.  
  
## Contrôles Line et Shape  
 Les contrôles Line et Shape encapsulent une bonne partie des méthodes graphiques contenues dans l'espace de noms <xref:System.Drawing>.  Cela vous permet de dessiner des lignes et des formes au cours d'une même étape sans devoir créer des objets graphiques, des stylets et des pinceaux.  Des techniques graphiques complexes telles que des dégradés peuvent par ailleurs être appliquées en définissant quelques propriétés.  
  
 Bien qu'il soit également possible de dessiner des lignes et des formes à l'aide de méthodes graphiques, l'utilisation des contrôles Line et Shape présente plusieurs avantages :  
  
-   Les méthodes graphiques peuvent uniquement être appelées au moment de l'exécution.  Les contrôles Line et Shape peuvent être ajoutés à un formulaire au moment du design.  Vous pouvez ainsi voir à quoi ils ressemblent et les positionner avec précision. Ils peuvent également être ajoutés au moment de l'exécution.  
  
-   Les contrôles Line et Shape sont sélectionnables au moment de l'exécution, en fournissant des événements tels que <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> et <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>.  Les sorties des méthodes graphiques ne sont pas sélectionnables et ne fournissent pas d'événements.  
  
-   Les contrôles Line et Shape fournissent des méthodes <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> et <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> qui vous permettent de contrôler leur ordre de plan au moment du design et de l'exécution.  L'ordre de plan des méthodes graphiques peut uniquement être contrôlé en modifiant leur ordre d'exécution au moment de l'exécution.  
  
-   Les contrôles Line et Shape sont des contrôles sans fenêtre ; ils ne possèdent pas de handles de fenêtre et utilisent par conséquent moins de ressources système.  
  
### Modèle objet  
 Les contrôles Line et Shape dérivent d'une classe <xref:Microsoft.VisualBasic.PowerPacks.Shape> de base qui définit leurs propriétés, méthodes et événements partagés.  
  
 L'illustration suivante montre la hiérarchie des objets Line et Shape.  
  
 ![Diagramme de la hiérarchie des objets Line et Shape](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Hiérarchie des objets Line et Shape  
  
 La classe <xref:Microsoft.VisualBasic.PowerPacks.LineShape> dérivée contient des propriétés, des méthodes et des événements propres aux lignes.  La classe <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> dérivée et la classe de base pour <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> et <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> et contient des propriétés, des méthodes et des événements communs à toutes les formes.  Vous pouvez également dériver de <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> pour créer vos propres contrôles `Shape`.  
  
 Les classes <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> et <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> peuvent être utilisées pour dessiner des cercles, des ovales, des rectangles et des rectangles à angles arrondis.  
  
 Lorsque vous ajoutez un contrôle Line ou Shape à un formulaire ou un conteneur, un objet <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> invisible est créé.  Le <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> joue le rôle de zone de dessin pour les formes au sein de chaque contrôle conteneur ; à chaque <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> correspond un <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> qui vous permet d'itérer au sein des contrôles Line et Shape.  Vous pouvez déplacer des formes d'un conteneur vers un autre par couper\-coller ou glisser\-déplacer.  Lorsque la dernière forme d'un conteneur est supprimée, le <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> l'est également.  
  
> [!NOTE]
>  Tous les contrôles conteneur ne prennent pas en charge les contrôles Line et Shape.  Vous ne pouvez pas héberger un contrôle Line ou Shape sur un <xref:System.Windows.Forms.TableLayoutPanel> ou un <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks>   
 [How to: Draw Lines with the LineShape Control](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)   
 [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)   
 [How to: Enable Tabbing Between Shapes](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)