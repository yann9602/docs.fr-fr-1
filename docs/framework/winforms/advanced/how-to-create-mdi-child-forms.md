---
title: "Comment : créer des formulaires MDI enfants"
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
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d0ee60e9b25ed4238ccdd738cd59a69876f6b55d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="eaa30-102">Comment : créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="eaa30-102">How to: Create MDI Child Forms</span></span>
<span data-ttu-id="eaa30-103">Formulaires MDI enfants constituent un élément essentiel de [Applications d’Interface multidocument (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), car ils représentent le centre de l’interaction utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eaa30-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>  
  
 <span data-ttu-id="eaa30-104">Dans la procédure suivante, vous allez créer un formulaire MDI enfant qui affiche un contrôle <xref:System.Windows.Forms.RichTextBox>, semblable à la plupart des applications de traitement de texte.</span><span class="sxs-lookup"><span data-stu-id="eaa30-104">In the following procedure, you will create MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="eaa30-105">La remplacement du contrôle <xref:System.Windows.Forms> par d'autres contrôles, tels que le contrôle <xref:System.Windows.Forms.DataGridView> ou une combinaison de contrôles, vous permet de créer des fenêtres MDI enfants (et, par extension, des applications MDI) avec diverses possibilités.</span><span class="sxs-lookup"><span data-stu-id="eaa30-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eaa30-106">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="eaa30-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="eaa30-107">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="eaa30-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="eaa30-108">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="eaa30-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-mdi-child-forms"></a><span data-ttu-id="eaa30-109">Pour créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="eaa30-109">To create MDI child forms</span></span>  
  
1.  <span data-ttu-id="eaa30-110">Créez un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="eaa30-110">Create a new Windows Forms project.</span></span> <span data-ttu-id="eaa30-111">Dans **les fenêtres Propriétés** pour le formulaire, définissez ses <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriété `true`et son `WindowsState` propriété `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="eaa30-111">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>  
  
     <span data-ttu-id="eaa30-112">Ainsi, vous désignez le formulaire comme le conteneur MDI des fenêtres enfants.</span><span class="sxs-lookup"><span data-stu-id="eaa30-112">This designates the form as an MDI container for child windows.</span></span>  
  
2.  <span data-ttu-id="eaa30-113">Faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> de la `Toolbox` vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="eaa30-113">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="eaa30-114">Définir son `Text` propriété **fichier**.</span><span class="sxs-lookup"><span data-stu-id="eaa30-114">Set its `Text` property to **File**.</span></span>  
  
3.  <span data-ttu-id="eaa30-115">Cliquez sur le bouton de sélection (...) à côté du **éléments** propriété, puis cliquez sur **ajouter** pour ajouter deux éléments de menu ToolStrip enfants outil.</span><span class="sxs-lookup"><span data-stu-id="eaa30-115">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="eaa30-116">Définir le `Text` propriété de ces éléments **nouveau** et **fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="eaa30-116">Set the `Text` property for these items to **New** and **Window**.</span></span>  
  
4.  <span data-ttu-id="eaa30-117">Dans **l’Explorateur de solutions**, cliquez sur le projet, pointez sur **ajouter**, puis sélectionnez **ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="eaa30-117">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>  
  
5.  <span data-ttu-id="eaa30-118">Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Windows Form** (dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou dans [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) ou **Application Windows Forms (.NET)** (dans [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) à partir de la **modèles** volet.</span><span class="sxs-lookup"><span data-stu-id="eaa30-118">In the **Add New Item** dialog box, select **Windows Form** (in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="eaa30-119">Dans le **nom** zone, nommez le formulaire **Form2**.</span><span class="sxs-lookup"><span data-stu-id="eaa30-119">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="eaa30-120">Cliquez sur le **ouvrir** pour ajouter le formulaire au projet.</span><span class="sxs-lookup"><span data-stu-id="eaa30-120">Click the **Open** button to add the form to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eaa30-121">Le formulaire MDI enfant que vous avez créé lors de cette étape est un Windows Form standard.</span><span class="sxs-lookup"><span data-stu-id="eaa30-121">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="eaa30-122">Il a donc une propriété <xref:System.Windows.Forms.Form.Opacity%2A>, ce qui vous permet de contrôler la transparence du formulaire.</span><span class="sxs-lookup"><span data-stu-id="eaa30-122">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="eaa30-123">Cependant, la propriété <xref:System.Windows.Forms.Form.Opacity%2A> a été conçue pour les fenêtres de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="eaa30-123">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="eaa30-124">Ne l'utilisez pas avec des formulaires MDI enfants, car des problèmes de peinture peuvent survenir.</span><span class="sxs-lookup"><span data-stu-id="eaa30-124">Do not use it with MDI child forms, as painting problems can occur.</span></span>  
  
     <span data-ttu-id="eaa30-125">Ce formulaire sera le modèle pour vos formulaires MDI enfants.</span><span class="sxs-lookup"><span data-stu-id="eaa30-125">This form will be the template for your MDI child forms.</span></span>  
  
     <span data-ttu-id="eaa30-126">Le **Concepteur Windows Forms** s’ouvre et affiche **Form2**.</span><span class="sxs-lookup"><span data-stu-id="eaa30-126">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>  
  
6.  <span data-ttu-id="eaa30-127">À partir de la **boîte à outils**, faites glisser un **RichTextBox** contrôle au formulaire.</span><span class="sxs-lookup"><span data-stu-id="eaa30-127">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>  
  
7.  <span data-ttu-id="eaa30-128">Dans le **propriétés** , configurez la `Anchor` propriété **en haut, gauche** et `Dock` propriété **remplir**.</span><span class="sxs-lookup"><span data-stu-id="eaa30-128">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>  
  
     <span data-ttu-id="eaa30-129">Ainsi, le contrôle <xref:System.Windows.Forms.RichTextBox> remplit complètement la zone de formulaire MDI enfant, même quand le formulaire est redimensionné.</span><span class="sxs-lookup"><span data-stu-id="eaa30-129">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>  
  
8.  <span data-ttu-id="eaa30-130">Double-cliquez sur le **nouveau** élément de menu pour créer un <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="eaa30-130">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>  
  
9. <span data-ttu-id="eaa30-131">Insérez du code semblable au suivant pour créer un nouveau formulaire MDI enfant lorsque l’utilisateur clique sur le **nouveau** élément de menu.</span><span class="sxs-lookup"><span data-stu-id="eaa30-131">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eaa30-132">Dans l'exemple suivant, le gestionnaire d'événements gère l'événement <xref:System.Windows.Forms.Control.Click> pour `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="eaa30-132">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="eaa30-133">Gardez à l’esprit que, selon les spécificités de votre architecture d’application, votre **nouveau** élément de menu ne peut pas être `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="eaa30-133">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     <span data-ttu-id="eaa30-134">Dans [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], ajoutez la directive `#include` suivante en haut de Form1.h :</span><span class="sxs-lookup"><span data-stu-id="eaa30-134">In [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], add the following `#include` directive at the top of Form1.h:</span></span>  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. <span data-ttu-id="eaa30-135">Dans la liste déroulante en haut de la **propriétés** fenêtre, sélectionnez la bande de menus qui correspond à la **fichier** bande de menus et définissez la <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriété dans la fenêtre de <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="eaa30-135">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
     <span data-ttu-id="eaa30-136">Cette opération activera le **fenêtre** menu pour maintenir une liste des fenêtres MDI enfants ouvertes avec une case à cocher en regard de la fenêtre enfant active.</span><span class="sxs-lookup"><span data-stu-id="eaa30-136">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>  
  
11. <span data-ttu-id="eaa30-137">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="eaa30-137">Press F5 to run the application.</span></span> <span data-ttu-id="eaa30-138">En sélectionnant **nouveau** à partir de la **fichier** menu, vous pouvez créer des formulaires MDI enfants dont la liste sont conservées dans le **fenêtre** élément de menu.</span><span class="sxs-lookup"><span data-stu-id="eaa30-138">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eaa30-139">Quand un formulaire MDI enfant a un composant <xref:System.Windows.Forms.MainMenu> (avec, généralement, une structure d'éléments de menu) et qu'il est ouvert dans un formulaire MDI parent qui a un composant <xref:System.Windows.Forms.MainMenu> (avec, généralement, une structure d'éléments de menu), les éléments de menu fusionnent automatiquement si vous avez défini la propriété <xref:System.Windows.Forms.MenuItem.MergeType%2A> (et, éventuellement, la propriété <xref:System.Windows.Forms.MenuItem.MergeOrder%2A>).</span><span class="sxs-lookup"><span data-stu-id="eaa30-139">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="eaa30-140">Affectez la valeur <xref:System.Windows.Forms.MenuMerge.MergeItems> à la propriété <xref:System.Windows.Forms.MenuItem.MergeType%2A> des deux composants <xref:System.Windows.Forms.MainMenu> et à tous les éléments de menu du formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="eaa30-140">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="eaa30-141">Définissez aussi la propriété <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> pour que les éléments de menu des deux menus apparaissent dans l'ordre souhaité.</span><span class="sxs-lookup"><span data-stu-id="eaa30-141">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="eaa30-142">De plus, sachez que quand vous fermez un formulaire MDI parent, chaque formulaire MDI enfant déclenche un événement <xref:System.Windows.Forms.Form.Closing> avant que l'événement <xref:System.Windows.Forms.Form.Closing> pour le parent MDI soit déclenché.</span><span class="sxs-lookup"><span data-stu-id="eaa30-142">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="eaa30-143">L'annulation de l'événement <xref:System.Windows.Forms.Form.Closing>  d'un enfant MDI n'empêchera pas le déclenchement de l'événement <xref:System.Windows.Forms.Form.Closing> du MDI parent. Toutefois, l'argument <xref:System.ComponentModel.CancelEventArgs> pour l'événement <xref:System.Windows.Forms.Form.Closing> du MDI parent prendra la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="eaa30-143">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="eaa30-144">Vous pouvez forcer la fermeture du MDI parent et de tous les formulaires MDI enfants en affectant la valeur `false` à l'argument <xref:System.ComponentModel.CancelEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="eaa30-144">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa30-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eaa30-145">See Also</span></span>  
 [<span data-ttu-id="eaa30-146">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="eaa30-146">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="eaa30-147">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="eaa30-147">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="eaa30-148">Guide pratique pour déterminer l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="eaa30-148">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="eaa30-149">Guide pratique pour envoyer des données à l’enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="eaa30-149">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="eaa30-150">Guide pratique pour réorganiser des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="eaa30-150">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
