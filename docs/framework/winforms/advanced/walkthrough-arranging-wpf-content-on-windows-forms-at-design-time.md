---
title: "Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afde62d07c009de4612aa44ebbd81b5a71ef36e5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="8f039-102">Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="8f039-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="8f039-103">Cette procédure pas à pas montre comment utiliser les fonctionnalités de disposition Windows Forms, telles que l’ancrage et les lignes d’alignement, pour disposer les contrôles WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="8f039-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>  
  
 <span data-ttu-id="8f039-104">Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f039-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="8f039-105">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="8f039-105">Create the project.</span></span>  
  
-   <span data-ttu-id="8f039-106">créer le contrôle WPF ;</span><span class="sxs-lookup"><span data-stu-id="8f039-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="8f039-107">héberger des contrôles WPF dans un panneau de disposition ;</span><span class="sxs-lookup"><span data-stu-id="8f039-107">Host WPF controls in a layout panel.</span></span>  
  
-   <span data-ttu-id="8f039-108">utiliser des lignes d'alignement pour aligner des contrôles WPF ;</span><span class="sxs-lookup"><span data-stu-id="8f039-108">Use snaplines to align WPF controls.</span></span>  
  
-   <span data-ttu-id="8f039-109">ancrer des contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="8f039-109">Anchor and dock WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f039-110">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="8f039-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8f039-111">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="8f039-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8f039-112">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8f039-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f039-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="8f039-113">Prerequisites</span></span>  
 <span data-ttu-id="8f039-114">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="8f039-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="8f039-115">.</span><span class="sxs-lookup"><span data-stu-id="8f039-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="8f039-116">Création du projet</span><span class="sxs-lookup"><span data-stu-id="8f039-116">Creating the Project</span></span>  
 <span data-ttu-id="8f039-117">La première étape consiste à créer le projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8f039-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f039-118">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8f039-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="8f039-119">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="8f039-119">To create the project</span></span>  
  
-   <span data-ttu-id="8f039-120">Créer un nouveau projet d’Application Windows Forms dans Visual Basic ou Visual c# nommé `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="8f039-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="8f039-121">Création du contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="8f039-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="8f039-122">Après avoir ajouté un contrôle WPF au projet, vous pouvez le disposer sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="8f039-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="8f039-123">Pour créer des contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="8f039-123">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="8f039-124">Ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF au projet.</span><span class="sxs-lookup"><span data-stu-id="8f039-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="8f039-125">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="8f039-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="8f039-126">Pour plus d’informations, consultez [procédure pas à pas : création WPF de contenu dans les Windows Forms au moment du Design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="8f039-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="8f039-127">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8f039-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="8f039-128">Pour plus d’informations, consultez [Comment : sélectionner et déplacer des éléments sur l’aire de conception](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="8f039-128">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="8f039-129">Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés `200`.</span><span class="sxs-lookup"><span data-stu-id="8f039-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="8f039-130">Affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur `Blue`.</span><span class="sxs-lookup"><span data-stu-id="8f039-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5.  <span data-ttu-id="8f039-131">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="8f039-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="8f039-132">Hébergement de contrôles WPF dans un panneau de disposition</span><span class="sxs-lookup"><span data-stu-id="8f039-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="8f039-133">Vous pouvez utiliser des contrôles WPF dans des panneaux de disposition de la même façon que vous utilisez d'autres contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8f039-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="8f039-134">Pour héberger des contrôles WPF dans un panneau de disposition</span><span class="sxs-lookup"><span data-stu-id="8f039-134">To host WPF controls in a layout panel</span></span>  
  
1.  <span data-ttu-id="8f039-135">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8f039-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="8f039-136">Dans le **boîte à outils**, faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="8f039-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3.  <span data-ttu-id="8f039-137">Sur le <xref:System.Windows.Forms.TableLayoutPanel> panneau des balises actives du contrôle, sélectionnez **supprimer la dernière ligne**.</span><span class="sxs-lookup"><span data-stu-id="8f039-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4.  <span data-ttu-id="8f039-138">Augmentez la largeur et la hauteur du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="8f039-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5.  <span data-ttu-id="8f039-139">Dans le **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` dans la première cellule de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f039-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="8f039-140">L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="8f039-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6.  <span data-ttu-id="8f039-141">Dans le **boîte à outils**, double-cliquez sur `UserControl1` pour créer une autre instance dans la deuxième cellule de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f039-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="8f039-142">Dans le **structure du Document** fenêtre, sélectionnez `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="8f039-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="8f039-143">Pour plus d’informations, consultez [fenêtre Structure du Document](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span><span class="sxs-lookup"><span data-stu-id="8f039-143">For more information, see [Document Outline Window](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span></span>  
  
8.  <span data-ttu-id="8f039-144">Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.Forms.Control.Padding%2A> propriété `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="8f039-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="8f039-145">Les deux contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés pour s'adapter à la nouvelle disposition.</span><span class="sxs-lookup"><span data-stu-id="8f039-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="8f039-146">Utilisation de lignes d'alignement pour aligner des contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="8f039-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="8f039-147">Les lignes d'alignement permettent d'aligner facilement les contrôles sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="8f039-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="8f039-148">Vous pouvez aussi utiliser des lignes d'alignement pour aligner vos contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="8f039-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="8f039-149">Pour plus d’informations, consultez [procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="8f039-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="8f039-150">Pour utiliser des lignes d'alignement pour aligner des contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="8f039-150">To use snaplines to align WPF controls</span></span>  
  
1.  <span data-ttu-id="8f039-151">À partir de la **boîte à outils**, faites glisser une instance de `UserControl1` sur le formulaire et placez-la dans l’espace sous le <xref:System.Windows.Forms.TableLayoutPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f039-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="8f039-152">L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="8f039-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2.  <span data-ttu-id="8f039-153">À l'aide des lignes d'alignement, alignez le bord gauche de `elementHost3` avec le bord gauche du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="8f039-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="8f039-154">À l'aide des lignes d'alignement, affectez à `elementHost3` la même largeur que celle du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="8f039-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="8f039-155">Déplacez `elementHost3` vers le contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce qu'une ligne d'alignement centrale apparaisse entre les contrôles.</span><span class="sxs-lookup"><span data-stu-id="8f039-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5.  <span data-ttu-id="8f039-156">Dans le **propriétés** fenêtre, définissez la valeur de la propriété de marge à `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="8f039-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6.  <span data-ttu-id="8f039-157">Déplacez le `elementHost3` hors du contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce que la ligne d'alignement centrale réapparaisse.</span><span class="sxs-lookup"><span data-stu-id="8f039-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="8f039-158">La ligne d'alignement centrale indique maintenant une marge de 20.</span><span class="sxs-lookup"><span data-stu-id="8f039-158">The center snapline now indicates a margin of 20.</span></span>  
  
7.  <span data-ttu-id="8f039-159">Déplacez `elementHost3` vers la droite jusqu'à ce que son bord gauche soit aligné avec le bord gauche de `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="8f039-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8.  <span data-ttu-id="8f039-160">Modifiez la largeur de `elementHost3` jusqu'à ce que son bord droit soit aligné avec le bord droit de `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="8f039-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="8f039-161">Ancrage de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="8f039-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="8f039-162">Un contrôle WPF hébergé sur un formulaire a le même comportement d'ancrage que d'autres contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8f039-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="8f039-163">Pour ancrer des contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="8f039-163">To anchor and dock WPF controls</span></span>  
  
1.  <span data-ttu-id="8f039-164">Sélectionnez `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="8f039-164">Select `elementHost1`.</span></span>  
  
2.  <span data-ttu-id="8f039-165">Dans le **propriétés** , configurez la <xref:System.Windows.Forms.Control.Anchor%2A> propriété **haut, bas, gauche, droite**.</span><span class="sxs-lookup"><span data-stu-id="8f039-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3.  <span data-ttu-id="8f039-166">Agrandissez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="8f039-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="8f039-167">Le contrôle `elementHost1` est redimensionné pour remplir la cellule.</span><span class="sxs-lookup"><span data-stu-id="8f039-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4.  <span data-ttu-id="8f039-168">Sélectionnez `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="8f039-168">Select `elementHost2`.</span></span>  
  
5.  <span data-ttu-id="8f039-169">Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="8f039-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="8f039-170">Le contrôle `elementHost2` est redimensionné pour remplir la cellule.</span><span class="sxs-lookup"><span data-stu-id="8f039-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6.  <span data-ttu-id="8f039-171">Sélectionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="8f039-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="8f039-172">Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="8f039-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8.  <span data-ttu-id="8f039-173">Sélectionnez `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="8f039-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="8f039-174">Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="8f039-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="8f039-175">Le contrôle `elementHost3` est redimensionné pour remplir l'espace restant sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="8f039-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="8f039-176">Redimensionnez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="8f039-176">Resize the form.</span></span>  
  
     <span data-ttu-id="8f039-177">Les trois contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés correctement.</span><span class="sxs-lookup"><span data-stu-id="8f039-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="8f039-178">Pour plus d’informations, consultez [Comment : ancrage et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="8f039-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f039-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f039-179">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="8f039-180">Guide pratique pour ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8f039-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="8f039-181">Guide pratique pour aligner un contrôle sur les bords des formulaires au moment du design</span><span class="sxs-lookup"><span data-stu-id="8f039-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="8f039-182">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="8f039-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="8f039-183">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="8f039-183">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="8f039-184">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="8f039-184">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="8f039-185">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="8f039-185">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
