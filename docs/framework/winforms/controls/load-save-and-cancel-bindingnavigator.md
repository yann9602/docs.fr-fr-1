---
title: "Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms"
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
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4bc4f53c404e3767b9f98ca5ab46b19db31f9c6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="13751-102">Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13751-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="13751-103">Le <xref:System.Windows.Forms.BindingNavigator> contrôle est à usage spécial <xref:System.Windows.Forms.ToolStrip> contrôle qui est destiné à la navigation et la manipulation de contrôles liés aux données sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="13751-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="13751-104">Car il s’agit d’un <xref:System.Windows.Forms.ToolStrip> (contrôle), le <xref:System.Windows.Forms.BindingNavigator> composant peut facilement être modifié pour inclure des commandes supplémentaires ou alternatives pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="13751-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="13751-105">Dans la procédure suivante, un <xref:System.Windows.Forms.TextBox> contrôle est lié aux données et le <xref:System.Windows.Forms.ToolStrip> contrôle qui est ajouté au formulaire est modifiée pour inclure charger, enregistrer et annuler des boutons.</span><span class="sxs-lookup"><span data-stu-id="13751-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="13751-106">Pour ajouter une charge, enregistrer et annuler des boutons pour le composant de BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="13751-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="13751-107">Ajoutez un contrôle <xref:System.Windows.Forms.TextBox> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="13751-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="13751-108">Lier à un <xref:System.Windows.Forms.BindingSource>, qui est lié à une source de données.</span><span class="sxs-lookup"><span data-stu-id="13751-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="13751-109">Pour cet exemple, le <xref:System.Windows.Forms.BindingSource> est lié à une base de données.</span><span class="sxs-lookup"><span data-stu-id="13751-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="13751-110">Une fois que l’adaptateur de jeu de données et de table sont générées, faites glisser un <xref:System.Windows.Forms.BindingNavigator> contrôle au formulaire.</span><span class="sxs-lookup"><span data-stu-id="13751-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="13751-111">Définir le <xref:System.Windows.Forms.BindingNavigator> du contrôle <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriété le <xref:System.Windows.Forms.BindingSource> sur le formulaire qui est lié aux contrôles.</span><span class="sxs-lookup"><span data-stu-id="13751-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="13751-112">Sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="13751-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="13751-113">Cliquez sur le glyphe de balise active (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) afin que la **tâches BindingNavigator** boîte de dialogue s’affiche et sélectionnez **modifier les éléments**.</span><span class="sxs-lookup"><span data-stu-id="13751-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="13751-114">Le **éditeur de collections Items** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="13751-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="13751-115">Dans le **éditeur de collections Items**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="13751-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="13751-116">Ajouter un <xref:System.Windows.Forms.ToolStripSeparator> et trois <xref:System.Windows.Forms.ToolStripButton> éléments en sélectionnant le type approprié de <xref:System.Windows.Forms.ToolStripItem> et en cliquant sur le **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="13751-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="13751-117">Définir le <xref:System.Windows.Forms.ToolStripItem.Name%2A> propriété des boutons pour**LoadButton**,**SaveButton**, et**CancelButton**, respectivement.</span><span class="sxs-lookup"><span data-stu-id="13751-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to**LoadButton**,**SaveButton**, and**CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="13751-118">Définir le <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété des boutons pour**charge** `,` **enregistrer**, et**Annuler**.</span><span class="sxs-lookup"><span data-stu-id="13751-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to**Load**`,` **Save**, and**Cancel**.</span></span>  
  
    4.  <span data-ttu-id="13751-119">Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété pour chacun des boutons pour**texte**.</span><span class="sxs-lookup"><span data-stu-id="13751-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to**Text**.</span></span> <span data-ttu-id="13751-120">Vous pouvez également définir cette propriété**Image**ou**ImageAndText**et définir l’image à afficher dans le <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="13751-120">Alternatively, you can set this property to**Image**or**ImageAndText**and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="13751-121">Cliquez sur **OK** pour fermer la boîte de dialogue. Les boutons sont ajoutés à la <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="13751-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="13751-122">Avec le bouton droit de la forme et choisissez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="13751-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="13751-123">Dans l’éditeur de Code, recherchez la ligne de code qui charge des données dans l’adaptateur de table.</span><span class="sxs-lookup"><span data-stu-id="13751-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="13751-124">Ce code a été généré lorsque vous configurez la liaison de données à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="13751-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="13751-125">Le code doit être semblable au suivant : `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="13751-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="13751-126">Il figurera très probablement être sous la forme <xref:System.Windows.Forms.Form.Load> événements.</span><span class="sxs-lookup"><span data-stu-id="13751-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="13751-127">Créer un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> l’événement de la**charge** <xref:System.Windows.Forms.ToolStripButton> créé précédemment et de placer ce code de chargement de données.</span><span class="sxs-lookup"><span data-stu-id="13751-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Load**<xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="13751-128">Votre code doit à présent ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="13751-128">Your code should now look similar to the following:</span></span>  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. <span data-ttu-id="13751-129">Créer un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> l’événement de la **enregistrer** <xref:System.Windows.Forms.ToolStripButton> vous avez créé précédemment et d’écrire du code pour mettre à jour les données dans la table, le contrôle est lié à.</span><span class="sxs-lookup"><span data-stu-id="13751-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="13751-130">Dans certains cas, le <xref:System.Windows.Forms.BindingNavigator> composant a déjà un**enregistrer** bouton, mais aucun code n’aura été généré par le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="13751-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a**Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="13751-131">Dans ce cas, vous pouvez placer le code précédent dans le <xref:System.Windows.Forms.ToolStripItem.Click> Gestionnaire d’événements pour ce bouton, au lieu de créer un nouveau bouton sur le <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="13751-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="13751-132">Toutefois, le bouton est désactivé par défaut, vous devez donc définir la <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriété du bouton `true` pour que le bouton fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="13751-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>  
  
12. <span data-ttu-id="13751-133">Créer un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> l’événement de la**Annuler** <xref:System.Windows.Forms.ToolStripButton> créé précédemment et d’écrire du code pour annuler toute modification apportée à l’enregistrement de données qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="13751-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Cancel**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="13751-134">Le <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> (méthode) est limitée à la ligne de données.</span><span class="sxs-lookup"><span data-stu-id="13751-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="13751-135">Enregistrez les modifications apportées lors de l’affichage de cet enregistrement individuel avant de naviguer jusqu'à l’enregistrement suivant.</span><span class="sxs-lookup"><span data-stu-id="13751-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13751-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13751-136">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="13751-137">BindingNavigator, contrôle</span><span class="sxs-lookup"><span data-stu-id="13751-137">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="13751-138">Vue d'ensemble du composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="13751-138">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
