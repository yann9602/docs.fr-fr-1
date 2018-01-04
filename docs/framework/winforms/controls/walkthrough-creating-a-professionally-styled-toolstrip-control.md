---
title: "Procédure pas à pas : création d'un contrôle ToolStrip de style professionnel"
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
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3d47f285643f0b989db9419392eed736d0efbea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="aeba6-102">Procédure pas à pas : création d'un contrôle ToolStrip de style professionnel</span><span class="sxs-lookup"><span data-stu-id="aeba6-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="aeba6-103">Vous pouvez donner à votre application <xref:System.Windows.Forms.ToolStrip> contrôle un aspect professionnel et le comportement en écrivant votre propre classe dérivée de la <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span><span class="sxs-lookup"><span data-stu-id="aeba6-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="aeba6-104">Cette procédure pas à pas montre comment utiliser <xref:System.Windows.Forms.ToolStrip> des contrôles pour créer un contrôle composite qui ressemble à la **volet de Navigation** fourni par Microsoft® Outlook®.</span><span class="sxs-lookup"><span data-stu-id="aeba6-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="aeba6-105">Les tâches suivantes sont illustrées dans cette procédure pas à pas :</span><span class="sxs-lookup"><span data-stu-id="aeba6-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="aeba6-106">Création d’un projet de bibliothèque de contrôles Windows.</span><span class="sxs-lookup"><span data-stu-id="aeba6-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="aeba6-107">Conception du contrôle StackView.</span><span class="sxs-lookup"><span data-stu-id="aeba6-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="aeba6-108">Implémentation d’un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="aeba6-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="aeba6-109">Lorsque vous avez terminé, vous devez un contrôle client personnalisé réutilisable avec l’apparence professionnelle d’un contrôle Microsoft Office® XP.</span><span class="sxs-lookup"><span data-stu-id="aeba6-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="aeba6-110">Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un professionnel contrôle ToolStrip de style](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="aeba6-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aeba6-111">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="aeba6-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="aeba6-112">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="aeba6-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="aeba6-113">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="aeba6-113">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aeba6-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="aeba6-114">Prerequisites</span></span>  
 <span data-ttu-id="aeba6-115">Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="aeba6-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="aeba6-116">Des autorisations suffisantes pour pouvoir créer et exécuter des projets d’application Windows Forms sur l’ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.</span><span class="sxs-lookup"><span data-stu-id="aeba6-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="aeba6-117">Création d’un projet de bibliothèque de contrôles Windows</span><span class="sxs-lookup"><span data-stu-id="aeba6-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="aeba6-118">La première étape consiste à créer le projet de bibliothèque de contrôles.</span><span class="sxs-lookup"><span data-stu-id="aeba6-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="aeba6-119">Pour créer le projet de bibliothèque de contrôle</span><span class="sxs-lookup"><span data-stu-id="aeba6-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="aeba6-120">Créer un nouveau projet de bibliothèque de contrôles Windows nommé `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="aeba6-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="aeba6-121">Dans **l’Explorateur de solutions**, supprimer le contrôle du projet par défaut en supprimant le fichier source nommé « UserControl1.cs » ou « UserControl1.vb », en fonction de la langue de votre choix.</span><span class="sxs-lookup"><span data-stu-id="aeba6-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="aeba6-122">Pour plus d’informations, consultez [NIB : Comment : exclure des éléments, de suppression et de suppression](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="aeba6-122">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="aeba6-123">Ajouter un nouveau <xref:System.Windows.Forms.UserControl> d’élément à la **StackViewLibrary** projet.</span><span class="sxs-lookup"><span data-stu-id="aeba6-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="aeba6-124">Nommez le nouveau fichier source base de `StackView`.</span><span class="sxs-lookup"><span data-stu-id="aeba6-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="aeba6-125">Conception du contrôle StackView</span><span class="sxs-lookup"><span data-stu-id="aeba6-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="aeba6-126">Le `StackView` contrôle est un contrôle composite avec un seul enfant <xref:System.Windows.Forms.ToolStrip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="aeba6-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="aeba6-127">Pour plus d’informations sur les contrôles composites, consultez [variétés de contrôles personnalisés de](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="aeba6-127">For more information about composite controls, see [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="aeba6-128">Pour concevoir le contrôle StackView</span><span class="sxs-lookup"><span data-stu-id="aeba6-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="aeba6-129">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.ToolStrip> contrôle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="aeba6-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="aeba6-130">Dans le **propriétés** , configurez le <xref:System.Windows.Forms.ToolStrip> les propriétés du contrôle conformément au tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="aeba6-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="aeba6-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="aeba6-131">Property</span></span>|<span data-ttu-id="aeba6-132">Valeur</span><span class="sxs-lookup"><span data-stu-id="aeba6-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="aeba6-133">Name</span><span class="sxs-lookup"><span data-stu-id="aeba6-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="aeba6-134">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="aeba6-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="aeba6-135">Station d' accueil</span><span class="sxs-lookup"><span data-stu-id="aeba6-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="aeba6-136">Police</span><span class="sxs-lookup"><span data-stu-id="aeba6-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="aeba6-137">GripStyle</span><span class="sxs-lookup"><span data-stu-id="aeba6-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="aeba6-138">LayoutStyle a été</span><span class="sxs-lookup"><span data-stu-id="aeba6-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="aeba6-139">Padding</span><span class="sxs-lookup"><span data-stu-id="aeba6-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="aeba6-140">RenderMode</span><span class="sxs-lookup"><span data-stu-id="aeba6-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="aeba6-141">Dans le Concepteur Windows Forms, cliquez sur le <xref:System.Windows.Forms.ToolStrip> du contrôle **ajouter** bouton et ajoutez un <xref:System.Windows.Forms.ToolStripButton> à la `stackStrip` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aeba6-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="aeba6-142">Dans le **propriétés** , configurez le <xref:System.Windows.Forms.ToolStripButton> les propriétés du contrôle conformément au tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="aeba6-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="aeba6-143">Propriété</span><span class="sxs-lookup"><span data-stu-id="aeba6-143">Property</span></span>|<span data-ttu-id="aeba6-144">Valeur</span><span class="sxs-lookup"><span data-stu-id="aeba6-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="aeba6-145">Name</span><span class="sxs-lookup"><span data-stu-id="aeba6-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="aeba6-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="aeba6-146">CheckOnClick</span></span>|<span data-ttu-id="aeba6-147">true</span><span class="sxs-lookup"><span data-stu-id="aeba6-147">true</span></span>|  
    |<span data-ttu-id="aeba6-148">CheckState</span><span class="sxs-lookup"><span data-stu-id="aeba6-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="aeba6-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="aeba6-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="aeba6-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="aeba6-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="aeba6-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="aeba6-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="aeba6-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="aeba6-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="aeba6-153">Marge</span><span class="sxs-lookup"><span data-stu-id="aeba6-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="aeba6-154">Padding</span><span class="sxs-lookup"><span data-stu-id="aeba6-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="aeba6-155">Texte</span><span class="sxs-lookup"><span data-stu-id="aeba6-155">Text</span></span>|<span data-ttu-id="aeba6-156">**Messagerie**</span><span class="sxs-lookup"><span data-stu-id="aeba6-156">**Mail**</span></span>|  
    |<span data-ttu-id="aeba6-157">TextAlign</span><span class="sxs-lookup"><span data-stu-id="aeba6-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="aeba6-158">Répétez l’étape 7 pour les trois autres <xref:System.Windows.Forms.ToolStripButton> contrôles.</span><span class="sxs-lookup"><span data-stu-id="aeba6-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="aeba6-159">Nommez les contrôles `calendarStackButton`, `contactsStackButton`, et `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="aeba6-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="aeba6-160">Définir la valeur de la <xref:System.Windows.Forms.Control.Text%2A> propriété **calendrier**, **Contacts**, et **tâches**, respectivement.</span><span class="sxs-lookup"><span data-stu-id="aeba6-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="aeba6-161">Gestion des événements</span><span class="sxs-lookup"><span data-stu-id="aeba6-161">Handling Events</span></span>  
 <span data-ttu-id="aeba6-162">Deux événements sont importantes pour rendre le `StackView` contrôle se comporte correctement.</span><span class="sxs-lookup"><span data-stu-id="aeba6-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="aeba6-163">Gérer les <xref:System.Windows.Forms.UserControl.Load> événement pour positionner le contrôle correctement.</span><span class="sxs-lookup"><span data-stu-id="aeba6-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="aeba6-164">Gérer les <xref:System.Windows.Forms.ToolStripItem.Click> événement pour chaque <xref:System.Windows.Forms.ToolStripButton> pour donner le `StackView` contrôlent le comportement d’état semblable à la <xref:System.Windows.Forms.RadioButton> contrôle.</span><span class="sxs-lookup"><span data-stu-id="aeba6-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="aeba6-165">Pour gérer des événements</span><span class="sxs-lookup"><span data-stu-id="aeba6-165">To handle events</span></span>  
  
1.  <span data-ttu-id="aeba6-166">Dans le Concepteur Windows Forms, sélectionnez le `StackView` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aeba6-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="aeba6-167">Dans le **propriétés** fenêtre, cliquez sur **événements**.</span><span class="sxs-lookup"><span data-stu-id="aeba6-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="aeba6-168">Double-cliquez sur l’événement Load pour générer le `StackView_Load` Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="aeba6-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="aeba6-169">Dans la méthode de gestionnaire d'événements `StackView_Load`, copiez et collez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="aeba6-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="aeba6-170">Dans le Concepteur Windows Forms, sélectionnez le `mailStackButton` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aeba6-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="aeba6-171">Dans le **propriétés** fenêtre, cliquez sur **événements**.</span><span class="sxs-lookup"><span data-stu-id="aeba6-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="aeba6-172">Double-cliquez sur l’événement Click.</span><span class="sxs-lookup"><span data-stu-id="aeba6-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="aeba6-173">Le Concepteur Windows Forms génère le `mailStackButton_Click` Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="aeba6-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="aeba6-174">Renommer le `mailStackButton_Click` Gestionnaire d’événements à `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="aeba6-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="aeba6-175">Pour plus d’informations, consultez [Comment : renommer un identificateur (Visual Basic)](http://msdn.microsoft.com/en-us/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span><span class="sxs-lookup"><span data-stu-id="aeba6-175">For more information, see [How to: Rename an Identifier (Visual Basic)](http://msdn.microsoft.com/en-us/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span></span>  
  
9. <span data-ttu-id="aeba6-176">Insérez le code suivant dans le `stackButton_Click` Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="aeba6-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="aeba6-177">Dans le Concepteur Windows Forms, sélectionnez le `calendarStackButton` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aeba6-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="aeba6-178">Dans le **propriétés** , configurez l’événement Click pour le `stackButton_Click` Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="aeba6-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="aeba6-179">Répétez les étapes 10 et 11 pour le `contactsStackButton` et `tasksStackButton` contrôles.</span><span class="sxs-lookup"><span data-stu-id="aeba6-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="aeba6-180">Définition d’icônes</span><span class="sxs-lookup"><span data-stu-id="aeba6-180">Defining Icons</span></span>  
 <span data-ttu-id="aeba6-181">Chaque `StackView` bouton a une icône associée.</span><span class="sxs-lookup"><span data-stu-id="aeba6-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="aeba6-182">Pour plus de commodité, chaque icône est représentée sous forme de chaîne codée en Base64 qui est désérialisée avant un <xref:System.Drawing.Bitmap> est créé à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="aeba6-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="aeba6-183">Dans un environnement de production, vous stockez des données bitmap en tant que ressource et vos icônes s’affichent dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aeba6-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="aeba6-184">Pour plus d’informations, consultez [Comment : ajouter des Images d’arrière-plan à des Windows Forms](http://msdn.microsoft.com/en-us/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span><span class="sxs-lookup"><span data-stu-id="aeba6-184">For more information, see [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/en-us/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="aeba6-185">Pour définir des icônes</span><span class="sxs-lookup"><span data-stu-id="aeba6-185">To define icons</span></span>  
  
1.  <span data-ttu-id="aeba6-186">Dans l’éditeur de Code, insérez le code suivant dans le `StackView` définition de classe.</span><span class="sxs-lookup"><span data-stu-id="aeba6-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="aeba6-187">Ce code initialise les bitmaps pour les <xref:System.Windows.Forms.ToolStripButton> icônes.</span><span class="sxs-lookup"><span data-stu-id="aeba6-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="aeba6-188">Ajoutez un appel à la `InitializeImages` méthode dans le `StackView` constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="aeba6-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="aeba6-189">Implémentation d’un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="aeba6-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="aeba6-190">Vous pouvez personnaliser la plupart des éléments de la `StackView` contrôler en implémentant une classe qui dérive de la <xref:System.Windows.Forms.ToolStripRenderer> classe.</span><span class="sxs-lookup"><span data-stu-id="aeba6-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="aeba6-191">Dans cette procédure, vous allez implémenter un <xref:System.Windows.Forms.ToolStripProfessionalRenderer> classe qui personnalise la poignée et dessine des arrière-plans dégradés pour le <xref:System.Windows.Forms.ToolStripButton> contrôles.</span><span class="sxs-lookup"><span data-stu-id="aeba6-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="aeba6-192">Pour implémenter un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="aeba6-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="aeba6-193">Insérez le code suivant dans le `StackView` définition du contrôle.</span><span class="sxs-lookup"><span data-stu-id="aeba6-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="aeba6-194">La définition de la `StackRenderer` classe, qui remplace le <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, et <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> méthodes pour produire une apparence personnalisée.</span><span class="sxs-lookup"><span data-stu-id="aeba6-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="aeba6-195">Dans le `StackView` constructeur du contrôle, créer une nouvelle instance de la `StackRenderer` classe et assignez-la à la `stackStrip` du contrôle <xref:System.Windows.Forms.ToolStrip.Renderer%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="aeba6-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="aeba6-196">Test du contrôle StackView</span><span class="sxs-lookup"><span data-stu-id="aeba6-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="aeba6-197">Le `StackView` contrôle dérive la <xref:System.Windows.Forms.UserControl> classe.</span><span class="sxs-lookup"><span data-stu-id="aeba6-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="aeba6-198">Par conséquent, vous pouvez tester le contrôle avec la **conteneur de Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="aeba6-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="aeba6-199">Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="aeba6-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="aeba6-200">Pour tester le contrôle StackView</span><span class="sxs-lookup"><span data-stu-id="aeba6-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="aeba6-201">Appuyez sur F5 pour générer le projet et démarrer le **conteneur de Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="aeba6-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="aeba6-202">Déplacez le pointeur sur les boutons de la `StackView` contrôler, puis cliquez sur un bouton pour visualiser l’apparence de son état sélectionné.</span><span class="sxs-lookup"><span data-stu-id="aeba6-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="aeba6-203">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="aeba6-203">Next Steps</span></span>  
 <span data-ttu-id="aeba6-204">Dans cette procédure pas à pas, vous avez créé un contrôle client personnalisé réutilisable avec l’apparence professionnelle d’un contrôle Microsoft Office XP.</span><span class="sxs-lookup"><span data-stu-id="aeba6-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="aeba6-205">Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStrip> famille de contrôles de nombreuses autres fins :</span><span class="sxs-lookup"><span data-stu-id="aeba6-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="aeba6-206">Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="aeba6-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="aeba6-207">Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="aeba6-207">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="aeba6-208">Créer un formulaire avec un menu standard automatiquement rempli.</span><span class="sxs-lookup"><span data-stu-id="aeba6-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="aeba6-209">Pour plus d’informations, consultez [procédure pas à pas : éléments de Menu Standard à un formulaire](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="aeba6-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="aeba6-210">Créer un formulaire d’interface (multidocument MDI) document avec l’ancrage <xref:System.Windows.Forms.ToolStrip> contrôles.</span><span class="sxs-lookup"><span data-stu-id="aeba6-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="aeba6-211">Pour plus d’informations, consultez [Comment : créer un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="aeba6-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeba6-212">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aeba6-212">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="aeba6-213">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="aeba6-213">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="aeba6-214">Comment : fournir des éléments de menu standard à un formulaire</span><span class="sxs-lookup"><span data-stu-id="aeba6-214">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
