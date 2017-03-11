---
title: "How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "OvalShape control"
  - "shapes, drawing"
  - "RectangleShape control"
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez utiliser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> pour tracer des cercles ou des ellipses sur un formulaire ou un conteneur au moment de la conception comme au moment de l'exécution.  Vous pouvez utiliser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> pour tracer des carrés, des rectangles ou des rectangles à angles arrondis sur un formulaire ou un conteneur.  Ce contrôle vous permet aussi de tracer des formes au moment de la conception ou au moment de l'exécution.  
  
 Vous pouvez personnaliser l'apparence d'une forme en modifiant la largeur, la couleur et le style de la bordure.  Si l'arrière\-plan d'une forme est transparent par défaut, vous pouvez le personnaliser avec une couleur unie, un motif, un dégradé \(transition d'une couleur à une autre\) ou une image.  
  
### Pour tracer une forme simple au moment de la conception  
  
1.  Faites glisser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ou <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> de l'onglet **Visual Basic PowerPacks** \(pour savoir comment les installer, consultez [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)\) de la **boîte à outils** vers un contrôle de formulaire ou de conteneur.  
  
2.  Faites glisser les poignées de redimensionnement et de déplacement pour redimensionner et positionner la forme.  
  
     Vous pouvez aussi redimensionner et positionner la forme en modifiant les propriétés `Size` et `Position` dans la fenêtre **Propriétés**.  
  
     Pour créer un rectangle à angles arrondis, sélectionnez la propriété `CornerRadius` dans la fenêtre **Propriétés** et affectez\-lui une valeur supérieure à 0.  
  
3.  Dans la fenêtre **Propriétés**, définissez éventuellement d'autres propriétés pour modifier l'apparence de la forme.  
  
### Pour tracer une forme simple au moment de l'exécution  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
2.  Dans la boîte de dialogue **Ajouter une référence**, sélectionnez **Microsoft.VisualBasic.PowerPacks.VS**, puis cliquez sur **OK**.  
  
3.  Dans l'**Éditeur de code**, ajoutez une instruction `Imports` ou `using` en haut du module :  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
4.  Ajoutez le code suivant dans une procédure `Event` :  
  
     [!code-cs[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerpacksShapeCS/VbPowerpacksShape.cs#1)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerpacksShape/VbPowerpacksShape.vb#1)]  
  
## Personnalisation des formes  
 Quand vous utilisez les paramètres par défaut, les contrôles <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> et <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> présentent une bordure noire unie d'un pixel de large et un arrière\-plan transparent.  Vous pouvez modifier la largeur, le style et la couleur de la bordure en définissant les propriétés.  D'autres propriétés vous permettent de modifier l'arrière\-plan d'une forme avec une couleur unie, un motif, un dégradé ou une image.  
  
 Avant de modifier l'arrière\-plan d'une forme, vous devez savoir comment les différentes propriétés interagissent.  
  
-   Le paramétrage de la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> n'a aucun effet dans la mesure où la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> n'a pas la valeur <xref:Microsoft.VisualBasic.PowerPacks.BackStyle>.  
  
-   Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> se substitue à <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> est définie avec une valeur de motif telle que <xref:Microsoft.VisualBasic.PowerPacks.FillStyle> ou <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>, le motif s'affiche dans <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.  L'arrière\-plan s'affiche dans <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, sous réserve que la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.BackStyle>.  
  
-   Pour afficher un dégradé, la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> doit avoir la valeur <xref:Microsoft.VisualBasic.PowerPacks.FillStyle>, tandis que la valeur de la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> doit être différente de <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle>.  
  
-   Quand une image est définie pour la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A>, celle\-ci se substitue à tous les autres paramètres d'arrière\-plan.  
  
#### Pour tracer un cercle avec une bordure personnalisée  
  
1.  Faites glisser le contrôle `OvalShape` de l'onglet **Visual Basic PowerPacks** de la **boîte à outils** vers un contrôle de formulaire ou de conteneur.  
  
2.  Dans la fenêtre **Propriétés**, dans la propriété `Size`, définissez des valeurs identiques pour `Height` et `Width`.  
  
3.  Affectez à la propriété `BorderColor` la couleur de votre choix.  
  
4.  Affectez à la propriété `BorderStyle` une autre valeur que `Solid`.  
  
5.  Définissez la taille que votre choix en pixels dans `BorderWidth`.  
  
#### Pour tracer un cercle avec un remplissage uni  
  
1.  Faites glisser le contrôle `OvalShape` de l'onglet **Visual Basic PowerPacks** de la **boîte à outils** vers un contrôle de formulaire ou de conteneur.  
  
2.  Dans la fenêtre **Propriétés**, dans la propriété `Size`, définissez des valeurs identiques pour `Height` et `Width`.  
  
3.  Définissez la couleur de votre choix dans la propriété `BackColor`.  
  
4.  Affectez à la propriété `BackStyle` la valeur `Opaque`.  
  
#### Pour tracer un cercle avec un remplissage à motif  
  
1.  Faites glisser le contrôle `OvalShape` de l'onglet **Visual Basic PowerPacks** de la **boîte à outils** vers un contrôle de formulaire ou de conteneur.  
  
2.  Dans la fenêtre **Propriétés**, dans la propriété `Size`, définissez des valeurs identiques pour `Height` et `Width`.  
  
3.  Définissez la couleur que vous voulez attribuer à l'arrière\-plan dans la propriété `BackColor`.  
  
4.  Affectez à la propriété `BackStyle` la valeur `Opaque`.  
  
5.  Définissez la couleur que vous voulez attribuer au motif dans la propriété `FillColor`.  
  
6.  Affectez à la propriété `FillStyle` une autre valeur que `Transparent` ou `Solid`.  
  
#### Pour tracer un cercle avec un dégradé  
  
1.  Faites glisser le contrôle `OvalShape` de l'onglet **Visual Basic PowerPacks** de la **boîte à outils** vers un contrôle de formulaire ou de conteneur.  
  
2.  Dans la fenêtre **Propriétés**, dans la propriété `Size`, définissez des valeurs identiques pour `Height` et `Width`.  
  
3.  Définissez la couleur que vous voulez attribuer à la couleur de départ dans la propriété `FillColor`.  
  
4.  Définissez la couleur que vous voulez attribuer à la couleur de fin dans la propriété `FillGradientColor`.  
  
5.  Affectez à la propriété `FillGradientStyle` une autre valeur que `None`.  
  
#### Pour tracer un cercle rempli par une image  
  
1.  Faites glisser le contrôle `OvalShape` de l'onglet **Visual Basic PowerPacks** de la **boîte à outils** vers un contrôle de formulaire ou de conteneur.  
  
2.  Dans la fenêtre **Propriétés**, dans la propriété `Size`, définissez des valeurs identiques pour `Height` et `Width`.  
  
3.  Sélectionnez la propriété `BackgroundImage` et cliquez sur le bouton représentant des **points de suspension** \(...\).  
  
4.  Dans la boîte de dialogue **Sélectionner une ressource**, sélectionnez l'image à afficher.  Si aucune ressource d'image n'est répertoriée, cliquez sur **Importer** pour accéder à l'emplacement d'une image.  
  
5.  Cliquez sur **OK** pour insérer l'image.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>   
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>   
 [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [How to: Draw Lines with the LineShape Control](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)