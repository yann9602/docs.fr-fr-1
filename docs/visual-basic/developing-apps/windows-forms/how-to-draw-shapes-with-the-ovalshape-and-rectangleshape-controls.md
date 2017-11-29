---
title: "Comment : dessiner des formes avec les contrôles OvalShape et RectangleShape (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53d91d10cc4735bbae521d17d05045cc7ea75fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Comment : dessiner des formes avec les contrôles OvalShape et RectangleShape (Visual Studio)
Vous pouvez utiliser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> pour tracer des cercles ou des ellipses sur un formulaire ou un conteneur au moment de la conception comme au moment de l'exécution. Vous pouvez utiliser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> pour tracer des carrés, des rectangles ou des rectangles à angles arrondis sur un formulaire ou un conteneur. Ce contrôle vous permet aussi de tracer des formes au moment de la conception ou au moment de l'exécution.  
  
 Vous pouvez personnaliser l'apparence d'une forme en modifiant la largeur, la couleur et le style de la bordure. Si l'arrière-plan d'une forme est transparent par défaut, vous pouvez le personnaliser avec une couleur unie, un motif, un dégradé (transition d'une couleur à une autre) ou une image.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Pour tracer une forme simple au moment de la conception  
  
1.  Faites glisser le <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ou <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> contrôler à partir de la **Visual Basic PowerPacks** onglet (pour installer, consultez [les contrôles Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) dans le **boîte à outils** pour un formulaire ou un contrôle conteneur.  
  
2.  Faites glisser les poignées de redimensionnement et de déplacement pour redimensionner et positionner la forme.  
  
     Vous pouvez également redimensionner et positionner la forme en modifiant le `Size` et `Position` propriétés dans le **propriétés** fenêtre.  
  
     Pour créer un rectangle à angles arrondis, sélectionnez le `CornerRadius` propriété dans le **propriétés** fenêtre et affectez-lui une valeur qui est supérieure à 0.  
  
3.  Dans le **propriétés** fenêtre, vous pouvez également définir les propriétés supplémentaires pour modifier l’apparence de la forme.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Pour tracer une forme simple au moment de l'exécution  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
2.  Dans le **ajouter une référence** boîte de dialogue, sélectionnez **Microsoft.VisualBasic.PowerPacks.VS**, puis cliquez sur **OK**.  
  
3.  Dans le **éditeur de Code**, ajoutez une `Imports` ou `using` instruction en haut du module :  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Ajoutez le code suivant dans une procédure `Event` :  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>Personnalisation des formes  
 Quand vous utilisez les paramètres par défaut, les contrôles <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> et <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> présentent une bordure noire unie d'un pixel de large et un arrière-plan transparent. Vous pouvez modifier la largeur, le style et la couleur de la bordure en définissant les propriétés. D'autres propriétés vous permettent de modifier l'arrière-plan d'une forme avec une couleur unie, un motif, un dégradé ou une image.  
  
 Avant de modifier l'arrière-plan d'une forme, vous devez savoir comment les différentes propriétés interagissent.  
  
-   Le paramétrage de la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> n'a aucun effet dans la mesure où la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> n'a pas la valeur <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> se substitue à <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> est définie avec une valeur de motif telle que <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> ou <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, le motif s'affiche dans <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>. L'arrière-plan s'affiche dans <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, sous réserve que la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Pour afficher un dégradé, la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> doit avoir la valeur <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, tandis que la valeur de la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> doit être différente de <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.  
  
-   Quand une image est définie pour la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A>, celle-ci se substitue à tous les autres paramètres d'arrière-plan.  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Pour tracer un cercle avec une bordure personnalisée  
  
1.  Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.  
  
2.  Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.  
  
3.  Affectez à la propriété `BorderColor` la couleur de votre choix.  
  
4.  Affectez à la propriété `BorderStyle` une autre valeur que `Solid`.  
  
5.  Définissez la taille que votre choix en pixels dans `BorderWidth`.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Pour tracer un cercle avec un remplissage uni  
  
1.  Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.  
  
2.  Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.  
  
3.  Affectez à la propriété `BackColor` la couleur de votre choix.  
  
4.  Affectez à la propriété `BackStyle` la valeur `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Pour tracer un cercle avec un remplissage à motif  
  
1.  Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.  
  
2.  Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.  
  
3.  Définissez la couleur que vous voulez attribuer à l'arrière-plan dans la propriété `BackColor`.  
  
4.  Affectez à la propriété `BackStyle` la valeur `Opaque`.  
  
5.  Définissez la couleur que vous voulez attribuer au motif dans la propriété `FillColor`.  
  
6.  Affectez à la propriété `FillStyle` une autre valeur que `Transparent` ou `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Pour tracer un cercle avec un dégradé  
  
1.  Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.  
  
2.  Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.  
  
3.  Définissez la couleur que vous voulez attribuer à la couleur de départ dans la propriété `FillColor`.  
  
4.  Définissez la couleur que vous voulez attribuer à la couleur de fin dans la propriété `FillGradientColor`.  
  
5.  Affectez à la propriété `FillGradientStyle` une autre valeur que `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Pour tracer un cercle rempli par une image  
  
1.  Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.  
  
2.  Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.  
  
3.  Sélectionnez le `BackgroundImage` propriété et cliquez sur le **points de suspension** bouton (...).  
  
4.  Dans le **sélectionner une ressource** boîte de dialogue, sélectionnez une image à afficher. Si aucune ressource d’image n’est répertorié, cliquez sur **importation** pour accéder à l’emplacement d’une image.  
  
5.  Cliquez sur **OK** pour insérer l’image.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [Introduction aux contrôles Line et Shape](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Guide pratique : dessiner des lignes avec le contrôle LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
