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
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a><span data-ttu-id="3469e-102">Comment : dessiner des formes avec les contrôles OvalShape et RectangleShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="3469e-102">How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)</span></span>
<span data-ttu-id="3469e-103">Vous pouvez utiliser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> pour tracer des cercles ou des ellipses sur un formulaire ou un conteneur au moment de la conception comme au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="3469e-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control to draw circles or ovals on a form or container, both at design time and at run time.</span></span> <span data-ttu-id="3469e-104">Vous pouvez utiliser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> pour tracer des carrés, des rectangles ou des rectangles à angles arrondis sur un formulaire ou un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3469e-104">You can use the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control to draw squares, rectangles, or rectangles with rounded corners on a form or container.</span></span> <span data-ttu-id="3469e-105">Ce contrôle vous permet aussi de tracer des formes au moment de la conception ou au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="3469e-105">You can also use this control to draw shapes both at design time and at run time.</span></span>  
  
 <span data-ttu-id="3469e-106">Vous pouvez personnaliser l'apparence d'une forme en modifiant la largeur, la couleur et le style de la bordure.</span><span class="sxs-lookup"><span data-stu-id="3469e-106">You can customize the appearance of a shape by changing the width, color, and style of the border.</span></span> <span data-ttu-id="3469e-107">Si l'arrière-plan d'une forme est transparent par défaut, vous pouvez le personnaliser avec une couleur unie, un motif, un dégradé (transition d'une couleur à une autre) ou une image.</span><span class="sxs-lookup"><span data-stu-id="3469e-107">The background of a shape is transparent by default; you can customize the background to display a solid color, a pattern, a gradient fill (transitioning from one color to another), or an image.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a><span data-ttu-id="3469e-108">Pour tracer une forme simple au moment de la conception</span><span class="sxs-lookup"><span data-stu-id="3469e-108">To draw a simple shape at design time</span></span>  
  
1.  <span data-ttu-id="3469e-109">Faites glisser le <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ou <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> contrôler à partir de la **Visual Basic PowerPacks** onglet (pour installer, consultez [les contrôles Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) dans le **boîte à outils** pour un formulaire ou un contrôle conteneur.</span><span class="sxs-lookup"><span data-stu-id="3469e-109">Drag the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> or <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control from the **Visual Basic PowerPacks** tab (to install, see [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md))in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="3469e-110">Faites glisser les poignées de redimensionnement et de déplacement pour redimensionner et positionner la forme.</span><span class="sxs-lookup"><span data-stu-id="3469e-110">Drag the sizing and move handles to size and position the shape.</span></span>  
  
     <span data-ttu-id="3469e-111">Vous pouvez également redimensionner et positionner la forme en modifiant le `Size` et `Position` propriétés dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3469e-111">You can also size and position the shape by changing the `Size` and `Position` properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="3469e-112">Pour créer un rectangle à angles arrondis, sélectionnez le `CornerRadius` propriété dans le **propriétés** fenêtre et affectez-lui une valeur qui est supérieure à 0.</span><span class="sxs-lookup"><span data-stu-id="3469e-112">To create a rectangle with rounded corners, select the `CornerRadius` property in the **Properties** window and set it to a value that is greater than 0.</span></span>  
  
3.  <span data-ttu-id="3469e-113">Dans le **propriétés** fenêtre, vous pouvez également définir les propriétés supplémentaires pour modifier l’apparence de la forme.</span><span class="sxs-lookup"><span data-stu-id="3469e-113">In the **Properties** window, optionally set additional properties to change the appearance of the shape.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a><span data-ttu-id="3469e-114">Pour tracer une forme simple au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="3469e-114">To draw a simple shape at run time</span></span>  
  
1.  <span data-ttu-id="3469e-115">Dans le menu **Projet**, cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="3469e-115">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="3469e-116">Dans le **ajouter une référence** boîte de dialogue, sélectionnez **Microsoft.VisualBasic.PowerPacks.VS**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3469e-116">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="3469e-117">Dans le **éditeur de Code**, ajoutez une `Imports` ou `using` instruction en haut du module :</span><span class="sxs-lookup"><span data-stu-id="3469e-117">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="3469e-118">Ajoutez le code suivant dans une procédure `Event` :</span><span class="sxs-lookup"><span data-stu-id="3469e-118">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a><span data-ttu-id="3469e-119">Personnalisation des formes</span><span class="sxs-lookup"><span data-stu-id="3469e-119">Customizing Shapes</span></span>  
 <span data-ttu-id="3469e-120">Quand vous utilisez les paramètres par défaut, les contrôles <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> et <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> présentent une bordure noire unie d'un pixel de large et un arrière-plan transparent.</span><span class="sxs-lookup"><span data-stu-id="3469e-120">When you use the default settings, the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls are displayed with a solid black border that is one pixel wide and a transparent background.</span></span> <span data-ttu-id="3469e-121">Vous pouvez modifier la largeur, le style et la couleur de la bordure en définissant les propriétés.</span><span class="sxs-lookup"><span data-stu-id="3469e-121">You can change the width, style, and color of the border by setting properties.</span></span> <span data-ttu-id="3469e-122">D'autres propriétés vous permettent de modifier l'arrière-plan d'une forme avec une couleur unie, un motif, un dégradé ou une image.</span><span class="sxs-lookup"><span data-stu-id="3469e-122">Additional properties enable you to change the background of a shape to a solid color, a pattern, a gradient fill, or an image.</span></span>  
  
 <span data-ttu-id="3469e-123">Avant de modifier l'arrière-plan d'une forme, vous devez savoir comment les différentes propriétés interagissent.</span><span class="sxs-lookup"><span data-stu-id="3469e-123">Before you change the background of a shape, you should know how several of the properties interact.</span></span>  
  
-   <span data-ttu-id="3469e-124">Le paramétrage de la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> n'a aucun effet dans la mesure où la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> n'a pas la valeur <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="3469e-124">The <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> property setting has no effect unless the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="3469e-125">Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> se substitue à <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="3469e-125">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> overrides the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span></span>  
  
-   <span data-ttu-id="3469e-126">Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> est définie avec une valeur de motif telle que <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> ou <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, le motif s'affiche dans <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="3469e-126">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to a pattern value such as <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> or <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, the pattern will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span></span> <span data-ttu-id="3469e-127">L'arrière-plan s'affiche dans <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, sous réserve que la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="3469e-127">The background will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, provided that the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="3469e-128">Pour afficher un dégradé, la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> doit avoir la valeur <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, tandis que la valeur de la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> doit être différente de <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="3469e-128">In order to display a gradient fill, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property must be set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> and the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> property must be set to a value other than <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span></span>  
  
-   <span data-ttu-id="3469e-129">Quand une image est définie pour la propriété <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A>, celle-ci se substitue à tous les autres paramètres d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="3469e-129">Setting the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> property to an image overrides all other background settings.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a><span data-ttu-id="3469e-130">Pour tracer un cercle avec une bordure personnalisée</span><span class="sxs-lookup"><span data-stu-id="3469e-130">To draw a circle that has a custom border</span></span>  
  
1.  <span data-ttu-id="3469e-131">Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3469e-131">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="3469e-132">Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.</span><span class="sxs-lookup"><span data-stu-id="3469e-132">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="3469e-133">Affectez à la propriété `BorderColor` la couleur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="3469e-133">Set the `BorderColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="3469e-134">Affectez à la propriété `BorderStyle` une autre valeur que `Solid`.</span><span class="sxs-lookup"><span data-stu-id="3469e-134">Set the `BorderStyle` property to any value other than `Solid`.</span></span>  
  
5.  <span data-ttu-id="3469e-135">Définissez la taille que votre choix en pixels dans `BorderWidth`.</span><span class="sxs-lookup"><span data-stu-id="3469e-135">Set the `BorderWidth` to the size that you want, in pixels.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a><span data-ttu-id="3469e-136">Pour tracer un cercle avec un remplissage uni</span><span class="sxs-lookup"><span data-stu-id="3469e-136">To draw a circle that has a solid fill</span></span>  
  
1.  <span data-ttu-id="3469e-137">Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3469e-137">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="3469e-138">Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.</span><span class="sxs-lookup"><span data-stu-id="3469e-138">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="3469e-139">Affectez à la propriété `BackColor` la couleur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="3469e-139">Set the `BackColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="3469e-140">Affectez à la propriété `BackStyle` la valeur `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="3469e-140">Set the `BackStyle` property to `Opaque`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a><span data-ttu-id="3469e-141">Pour tracer un cercle avec un remplissage à motif</span><span class="sxs-lookup"><span data-stu-id="3469e-141">To draw a circle that has a patterned fill</span></span>  
  
1.  <span data-ttu-id="3469e-142">Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3469e-142">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="3469e-143">Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.</span><span class="sxs-lookup"><span data-stu-id="3469e-143">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="3469e-144">Définissez la couleur que vous voulez attribuer à l'arrière-plan dans la propriété `BackColor`.</span><span class="sxs-lookup"><span data-stu-id="3469e-144">Set the `BackColor` property to the color that you want for the background.</span></span>  
  
4.  <span data-ttu-id="3469e-145">Affectez à la propriété `BackStyle` la valeur `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="3469e-145">Set the `BackStyle` property to `Opaque`.</span></span>  
  
5.  <span data-ttu-id="3469e-146">Définissez la couleur que vous voulez attribuer au motif dans la propriété `FillColor`.</span><span class="sxs-lookup"><span data-stu-id="3469e-146">Set the `FillColor` property to the color that you want for the pattern.</span></span>  
  
6.  <span data-ttu-id="3469e-147">Affectez à la propriété `FillStyle` une autre valeur que `Transparent` ou `Solid`.</span><span class="sxs-lookup"><span data-stu-id="3469e-147">Set the `FillStyle` property to any value other than `Transparent` or `Solid`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a><span data-ttu-id="3469e-148">Pour tracer un cercle avec un dégradé</span><span class="sxs-lookup"><span data-stu-id="3469e-148">To draw a circle that has a gradient fill</span></span>  
  
1.  <span data-ttu-id="3469e-149">Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3469e-149">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="3469e-150">Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.</span><span class="sxs-lookup"><span data-stu-id="3469e-150">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="3469e-151">Définissez la couleur que vous voulez attribuer à la couleur de départ dans la propriété `FillColor`.</span><span class="sxs-lookup"><span data-stu-id="3469e-151">Set the `FillColor` property to the color that you want for the starting color.</span></span>  
  
4.  <span data-ttu-id="3469e-152">Définissez la couleur que vous voulez attribuer à la couleur de fin dans la propriété `FillGradientColor`.</span><span class="sxs-lookup"><span data-stu-id="3469e-152">Set the `FillGradientColor` property to the color that you want for the ending color.</span></span>  
  
5.  <span data-ttu-id="3469e-153">Affectez à la propriété `FillGradientStyle` une autre valeur que `None`.</span><span class="sxs-lookup"><span data-stu-id="3469e-153">Set the `FillGradientStyle` property to a value other than `None`.</span></span>  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a><span data-ttu-id="3469e-154">Pour tracer un cercle rempli par une image</span><span class="sxs-lookup"><span data-stu-id="3469e-154">To draw a circle that is filled with an image</span></span>  
  
1.  <span data-ttu-id="3469e-155">Faites glisser le `OvalShape` contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.</span><span class="sxs-lookup"><span data-stu-id="3469e-155">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="3469e-156">Dans le **propriétés** fenêtre, dans le `Size` propriété, la valeur `Height` et `Width` valeurs identiques pour.</span><span class="sxs-lookup"><span data-stu-id="3469e-156">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="3469e-157">Sélectionnez le `BackgroundImage` propriété et cliquez sur le **points de suspension** bouton (...).</span><span class="sxs-lookup"><span data-stu-id="3469e-157">Select the `BackgroundImage` property and click the **ellipsis** button (...).</span></span>  
  
4.  <span data-ttu-id="3469e-158">Dans le **sélectionner une ressource** boîte de dialogue, sélectionnez une image à afficher.</span><span class="sxs-lookup"><span data-stu-id="3469e-158">In the **Select Resource** dialog box, select an image to display.</span></span> <span data-ttu-id="3469e-159">Si aucune ressource d’image n’est répertorié, cliquez sur **importation** pour accéder à l’emplacement d’une image.</span><span class="sxs-lookup"><span data-stu-id="3469e-159">If no image resources are listed, click **Import** to browse to the location of an image.</span></span>  
  
5.  <span data-ttu-id="3469e-160">Cliquez sur **OK** pour insérer l’image.</span><span class="sxs-lookup"><span data-stu-id="3469e-160">Click **OK** to insert the image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3469e-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3469e-161">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [<span data-ttu-id="3469e-162">Introduction aux contrôles Line et Shape</span><span class="sxs-lookup"><span data-stu-id="3469e-162">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="3469e-163">Guide pratique : dessiner des lignes avec le contrôle LineShape</span><span class="sxs-lookup"><span data-stu-id="3469e-163">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
