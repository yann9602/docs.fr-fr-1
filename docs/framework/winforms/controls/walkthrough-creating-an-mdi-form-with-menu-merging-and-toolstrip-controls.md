---
title: "Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip"
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
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b170c3e3311dbbfb070a66107bd4f22407647bae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="63721-102">Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="63721-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="63721-103">L'espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> prend en charge plusieurs applications MDI (Multiple Document Interface) et le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge la fusion de menus.</span><span class="sxs-lookup"><span data-stu-id="63721-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="63721-104">Les formulaires MDI peuvent également contenir des contrôles <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="63721-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="63721-105">Cette procédure pas à pas montre comment utiliser <xref:System.Windows.Forms.ToolStripPanel> les contrôles dans un formulaire MDI.</span><span class="sxs-lookup"><span data-stu-id="63721-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="63721-106">Le formulaire prend également en charge la fusion de menus avec les menus enfants.</span><span class="sxs-lookup"><span data-stu-id="63721-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="63721-107">Les tâches suivantes sont illustrées dans cette procédure pas à pas :</span><span class="sxs-lookup"><span data-stu-id="63721-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="63721-108">Création d’un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="63721-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="63721-109">Création du menu principal de votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-109">Creating the main menu for your form.</span></span> <span data-ttu-id="63721-110">Le nom réel du menu varient.</span><span class="sxs-lookup"><span data-stu-id="63721-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="63721-111">Ajout de la <xref:System.Windows.Forms.ToolStripPanel> le contrôle à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="63721-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="63721-112">Création d’un formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="63721-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="63721-113">Réorganiser les <xref:System.Windows.Forms.ToolStripPanel> par ordre de plan des contrôles.</span><span class="sxs-lookup"><span data-stu-id="63721-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="63721-114">Lorsque vous avez terminé, vous aurez un formulaire MDI qui prend en charge la fusion de menus et d’être déplacés <xref:System.Windows.Forms.ToolStrip> contrôles.</span><span class="sxs-lookup"><span data-stu-id="63721-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="63721-115">Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="63721-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63721-116">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="63721-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="63721-117">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="63721-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="63721-118">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="63721-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="63721-119">Prérequis</span><span class="sxs-lookup"><span data-stu-id="63721-119">Prerequisites</span></span>  
 <span data-ttu-id="63721-120">Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="63721-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="63721-121">Des autorisations suffisantes pour pouvoir créer et exécuter des projets d’application Windows Forms sur l’ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.</span><span class="sxs-lookup"><span data-stu-id="63721-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="63721-122">Création du projet</span><span class="sxs-lookup"><span data-stu-id="63721-122">Creating the Project</span></span>  
 <span data-ttu-id="63721-123">La première étape consiste à créer le projet et à configurer le formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="63721-124">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="63721-124">To create the project</span></span>  
  
1.  <span data-ttu-id="63721-125">Créez un projet d’Application Windows appelé **feuille MDI**.</span><span class="sxs-lookup"><span data-stu-id="63721-125">Create a Windows Application project called **MdiForm**.</span></span>  
  
     <span data-ttu-id="63721-126">Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="63721-126">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="63721-127">Dans le Concepteur Windows Forms, sélectionnez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-127">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="63721-128">Dans la fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.Form.IsMdiContainer%2A> à `true`.</span><span class="sxs-lookup"><span data-stu-id="63721-128">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="63721-129">Création du Menu principal</span><span class="sxs-lookup"><span data-stu-id="63721-129">Creating the Main Menu</span></span>  
 <span data-ttu-id="63721-130">Le formulaire MDI parent contient le menu principal.</span><span class="sxs-lookup"><span data-stu-id="63721-130">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="63721-131">Le menu principal possède un élément de menu nommé **fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="63721-131">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="63721-132">Avec la **fenêtre** l’élément de menu, vous pouvez créer des formulaires enfants.</span><span class="sxs-lookup"><span data-stu-id="63721-132">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="63721-133">Éléments de menu à partir de formulaires enfants sont fusionnés dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="63721-133">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="63721-134">Pour créer le menu principal</span><span class="sxs-lookup"><span data-stu-id="63721-134">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="63721-135">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.MenuStrip> contrôle vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="63721-136">Ajouter un <xref:System.Windows.Forms.ToolStripMenuItem> à la <xref:System.Windows.Forms.MenuStrip> contrôler et nommez-le **fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="63721-136">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="63721-137">Sélectionnez le contrôle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="63721-137">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="63721-138">Dans la fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriété `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="63721-138">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="63721-139">Ajouter un sous-élément à la **fenêtre** élément de menu, puis nommez le sous-élément **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="63721-139">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="63721-140">Dans la fenêtre Propriétés, cliquez sur **événements**.</span><span class="sxs-lookup"><span data-stu-id="63721-140">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="63721-141">Double-cliquez sur le <xref:System.Windows.Forms.ToolStripItem.Click> événement.</span><span class="sxs-lookup"><span data-stu-id="63721-141">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="63721-142">Le Concepteur Windows Forms génère un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> événement.</span><span class="sxs-lookup"><span data-stu-id="63721-142">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="63721-143">Insérez le code suivant dans le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="63721-143">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="63721-144">Ajout du contrôle ToolStripPanel à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="63721-144">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="63721-145">Lorsque vous utilisez <xref:System.Windows.Forms.MenuStrip> contrôles avec un formulaire MDI doit avoir le <xref:System.Windows.Forms.ToolStripPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="63721-145">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="63721-146">Vous devez ajouter le <xref:System.Windows.Forms.ToolStripPanel> le contrôle à la **boîte à outils** pour générer votre formulaire MDI dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="63721-146">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="63721-147">Pour ajouter le contrôle ToolStripPanel à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="63721-147">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="63721-148">Ouvrez le **boîte à outils**, puis cliquez sur le **tous les Windows Forms** onglet pour afficher les contrôles Windows Forms disponibles.</span><span class="sxs-lookup"><span data-stu-id="63721-148">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="63721-149">Avec le bouton droit pour ouvrir le menu contextuel, puis sélectionnez **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="63721-149">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="63721-150">Dans le **choisir des éléments de boîte à outils** boîte de dialogue, faites défiler vers le bas la **nom** colonne jusqu'à ce que vous trouviez **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="63721-150">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="63721-151">Activez la case à cocher en **ToolStripPanel**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="63721-151">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="63721-152">Le <xref:System.Windows.Forms.ToolStripPanel> contrôle s’affiche dans le **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="63721-152">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="63721-153">Création d’un formulaire enfant</span><span class="sxs-lookup"><span data-stu-id="63721-153">Creating a Child Form</span></span>  
 <span data-ttu-id="63721-154">Dans cette procédure, vous allez définir une classe de formulaire enfant séparée qui a son propre <xref:System.Windows.Forms.MenuStrip> contrôle.</span><span class="sxs-lookup"><span data-stu-id="63721-154">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="63721-155">Les éléments de menu pour ce formulaire sont fusionnées avec celles du formulaire parent.</span><span class="sxs-lookup"><span data-stu-id="63721-155">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="63721-156">Pour définir un formulaire enfant</span><span class="sxs-lookup"><span data-stu-id="63721-156">To define a child form</span></span>  
  
1.  <span data-ttu-id="63721-157">Ajoutez un nouveau formulaire nommé `ChildForm` au projet.</span><span class="sxs-lookup"><span data-stu-id="63721-157">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="63721-158">Pour plus d’informations, consultez [Comment : ajouter des Windows Forms à un projet](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="63721-158">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="63721-159">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.MenuStrip> contrôle dans le formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="63721-159">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="63721-160">Cliquez sur le <xref:System.Windows.Forms.MenuStrip> glyphe de balise active du contrôle (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), puis sélectionnez **modifier les éléments**.</span><span class="sxs-lookup"><span data-stu-id="63721-160">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="63721-161">Dans le **éditeur de collections Items** boîte de dialogue zone, ajoutez une nouvelle <xref:System.Windows.Forms.ToolStripMenuItem> nommé **ChildMenuItem** au menu enfant.</span><span class="sxs-lookup"><span data-stu-id="63721-161">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="63721-162">Pour plus d’informations, consultez [éditeur de collections d’éléments ToolStrip](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span><span class="sxs-lookup"><span data-stu-id="63721-162">For more information, see [ToolStrip Items Collection Editor](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="63721-163">Test du formulaire</span><span class="sxs-lookup"><span data-stu-id="63721-163">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="63721-164">Pour tester votre formulaire</span><span class="sxs-lookup"><span data-stu-id="63721-164">To test your form</span></span>  
  
1.  <span data-ttu-id="63721-165">Appuyez sur F5 pour compiler et exécuter votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-165">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="63721-166">Cliquez sur le **fenêtre** élément de menu pour ouvrir le menu, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="63721-166">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="63721-167">Un nouveau formulaire enfant est créé dans la zone du formulaire MDI client.</span><span class="sxs-lookup"><span data-stu-id="63721-167">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="63721-168">Les menus du formulaire enfant sont fusionné avec le menu principal.</span><span class="sxs-lookup"><span data-stu-id="63721-168">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="63721-169">Fermez le formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="63721-169">Close the child form.</span></span>  
  
     <span data-ttu-id="63721-170">Les menus du formulaire enfant sont supprimé dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="63721-170">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="63721-171">Cliquez sur **nouveau** plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="63721-171">Click **New** several times.</span></span>  
  
     <span data-ttu-id="63721-172">Les formulaires enfants sont automatiquement répertoriés sous la W**fenêtre** élément de menu, car le <xref:System.Windows.Forms.MenuStrip> du contrôle <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> est affectée.</span><span class="sxs-lookup"><span data-stu-id="63721-172">The child forms are automatically listed under the W**indow** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="63721-173">Ajout d’un Support ToolStrip</span><span class="sxs-lookup"><span data-stu-id="63721-173">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="63721-174">Dans cette procédure, vous allez ajouter quatre <xref:System.Windows.Forms.ToolStrip> contrôles au formulaire parent MDI.</span><span class="sxs-lookup"><span data-stu-id="63721-174">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="63721-175">Chaque <xref:System.Windows.Forms.ToolStrip> contrôle est ajouté à l’intérieur d’un <xref:System.Windows.Forms.ToolStripPanel> contrôle, qui est ancré sur le bord de l’écran.</span><span class="sxs-lookup"><span data-stu-id="63721-175">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="63721-176">Pour ajouter des contrôles ToolStrip au formulaire parent MDI</span><span class="sxs-lookup"><span data-stu-id="63721-176">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="63721-177">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.ToolStripPanel> contrôle vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-177">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="63721-178">Avec la <xref:System.Windows.Forms.ToolStripPanel> contrôle sélectionné, double-cliquez sur le <xref:System.Windows.Forms.ToolStrip> contrôler dans le **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="63721-178">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="63721-179">A <xref:System.Windows.Forms.ToolStrip> contrôle est créé dans le <xref:System.Windows.Forms.ToolStripPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="63721-179">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="63721-180">Sélectionnez le contrôle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="63721-180">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="63721-181">Dans la fenêtre Propriétés, modifiez la valeur du contrôle <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="63721-181">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="63721-182">Le <xref:System.Windows.Forms.ToolStripPanel> contrôler s’ancre sur le côté gauche de l’écran, sous le menu principal.</span><span class="sxs-lookup"><span data-stu-id="63721-182">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="63721-183">La zone cliente MDI est redimensionné pour s’ajuster à la <xref:System.Windows.Forms.ToolStripPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="63721-183">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="63721-184">Répétez les étapes 1 à 4.</span><span class="sxs-lookup"><span data-stu-id="63721-184">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="63721-185">Ancrer la nouvelle <xref:System.Windows.Forms.ToolStripPanel> contrôle en haut du formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-185">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="63721-186">Le <xref:System.Windows.Forms.ToolStripPanel> contrôle est ancré sous le menu principal, mais à droite de la première <xref:System.Windows.Forms.ToolStripPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="63721-186">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="63721-187">Cette étape illustre l’importance de l’ordre de plan positionner correctement <xref:System.Windows.Forms.ToolStripPanel> contrôles.</span><span class="sxs-lookup"><span data-stu-id="63721-187">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="63721-188">Répétez les étapes 1 à 4 pour deux autres <xref:System.Windows.Forms.ToolStripPanel> contrôles.</span><span class="sxs-lookup"><span data-stu-id="63721-188">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="63721-189">Ancrer la nouvelle <xref:System.Windows.Forms.ToolStripPanel> contrôles à droite et en bas du formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-189">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="63721-190">Organisation des contrôles ToolStripPanel par ordre de plan</span><span class="sxs-lookup"><span data-stu-id="63721-190">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="63721-191">La position d’une fenêtre fixe <xref:System.Windows.Forms.ToolStripPanel> contrôle sur votre formulaire MDI est déterminée par la position du contrôle dans l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="63721-191">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="63721-192">Vous pouvez facilement réorganiser l’ordre de plan de vos contrôles dans la fenêtre Structure du Document.</span><span class="sxs-lookup"><span data-stu-id="63721-192">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="63721-193">Pour organiser les contrôles ToolStripPanel suivant l’ordre de plan</span><span class="sxs-lookup"><span data-stu-id="63721-193">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="63721-194">Dans le **vue** menu, cliquez sur **autres fenêtres**, puis cliquez sur **structure du Document**.</span><span class="sxs-lookup"><span data-stu-id="63721-194">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="63721-195">La disposition de votre <xref:System.Windows.Forms.ToolStripPanel> contrôles à partir de la procédure précédente n’est pas standard.</span><span class="sxs-lookup"><span data-stu-id="63721-195">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="63721-196">Il s’agit, car l’ordre de plan n’est pas correct.</span><span class="sxs-lookup"><span data-stu-id="63721-196">This is because the z-order is not correct.</span></span> <span data-ttu-id="63721-197">Utilisez la fenêtre Structure du Document pour modifier l’ordre de plan des contrôles.</span><span class="sxs-lookup"><span data-stu-id="63721-197">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="63721-198">Dans la fenêtre Structure du Document, sélectionnez **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="63721-198">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="63721-199">Cliquez sur le bouton de flèche vers le bas à plusieurs reprises, jusqu'à ce que **ToolStripPanel4** figure au bas de la liste.</span><span class="sxs-lookup"><span data-stu-id="63721-199">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="63721-200">Le **ToolStripPanel4** contrôle est ancré en bas de l’écran, sous les autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="63721-200">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="63721-201">Sélectionnez **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="63721-201">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="63721-202">Cliquez une fois sur le bouton de flèche vers le bas pour positionner le troisième contrôle dans la liste.</span><span class="sxs-lookup"><span data-stu-id="63721-202">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="63721-203">Le **ToolStripPanel2** contrôle est ancrée en haut de l’écran, sous le menu principal et au-dessus des autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="63721-203">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="63721-204">Sélectionnez différents contrôles dans le **structure du Document** fenêtre et les déplacer à différents endroits dans l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="63721-204">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="63721-205">Notez l’effet de l’ordre de plan sur la position des contrôles ancrés.</span><span class="sxs-lookup"><span data-stu-id="63721-205">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="63721-206">Utilisez CTRL + Z ou **Annuler** sur la **modifier** menu pour annuler vos modifications.</span><span class="sxs-lookup"><span data-stu-id="63721-206">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="63721-207">Point de contrôle</span><span class="sxs-lookup"><span data-stu-id="63721-207">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="63721-208">Pour tester votre formulaire</span><span class="sxs-lookup"><span data-stu-id="63721-208">To test your form</span></span>  
  
1.  <span data-ttu-id="63721-209">Appuyez sur F5 pour compiler et exécuter votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-209">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="63721-210">Cliquez sur la poignée d’un <xref:System.Windows.Forms.ToolStrip> contrôler et faites glisser le contrôle à différents endroits dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="63721-210">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="63721-211">Vous pouvez faire glisser un <xref:System.Windows.Forms.ToolStrip> contrôle à partir d’un <xref:System.Windows.Forms.ToolStripPanel> contrôle à un autre.</span><span class="sxs-lookup"><span data-stu-id="63721-211">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="63721-212">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="63721-212">Next Steps</span></span>  
 <span data-ttu-id="63721-213">Dans cette procédure pas à pas, vous avez créé un formulaire MDI parent avec <xref:System.Windows.Forms.ToolStrip> de contrôles et de la fusion de menus.</span><span class="sxs-lookup"><span data-stu-id="63721-213">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="63721-214">Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStrip> famille de contrôles de nombreuses autres fins :</span><span class="sxs-lookup"><span data-stu-id="63721-214">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="63721-215">Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="63721-215">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="63721-216">Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="63721-216">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="63721-217">Créer un formulaire avec un menu standard automatiquement rempli.</span><span class="sxs-lookup"><span data-stu-id="63721-217">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="63721-218">Pour plus d’informations, consultez [procédure pas à pas : éléments de Menu Standard à un formulaire](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="63721-218">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="63721-219">Donnez à votre <xref:System.Windows.Forms.ToolStrip> contrôle un aspect professionnel.</span><span class="sxs-lookup"><span data-stu-id="63721-219">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="63721-220">Pour plus d’informations, consultez [Comment : définir le convertisseur ToolStrip pour une Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="63721-220">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63721-221">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63721-221">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="63721-222">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="63721-222">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="63721-223">Guide pratique pour créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="63721-223">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="63721-224">Guide pratique pour insérer un MenuStrip dans un menu déroulant MDI</span><span class="sxs-lookup"><span data-stu-id="63721-224">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="63721-225">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="63721-225">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
