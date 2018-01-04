---
title: "Procédure pas à pas : application de styles au contenu WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fa4772ebb321f927087fe13d0d50a6ae8145e55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="ebaf9-102">Procédure pas à pas : application de styles au contenu WPF</span><span class="sxs-lookup"><span data-stu-id="ebaf9-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="ebaf9-103">Cette procédure pas à pas montre comment appliquer des styles à un contrôle WPF (Windows Presentation Foundation) hébergé sur un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="ebaf9-104">Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="ebaf9-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="ebaf9-105">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="ebaf9-105">Create the project.</span></span>  
  
-   <span data-ttu-id="ebaf9-106">créer le type de contrôle WPF ;</span><span class="sxs-lookup"><span data-stu-id="ebaf9-106">Create the WPF control type.</span></span>  
  
-   <span data-ttu-id="ebaf9-107">appliquer un style au contrôle WPF.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-107">Apply a style to the WPF control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebaf9-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ebaf9-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="ebaf9-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ebaf9-110">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ebaf9-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ebaf9-111">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ebaf9-111">Prerequisites</span></span>  
 <span data-ttu-id="ebaf9-112">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="ebaf9-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="ebaf9-113">.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="ebaf9-114">Création du projet</span><span class="sxs-lookup"><span data-stu-id="ebaf9-114">Creating the Project</span></span>  
 <span data-ttu-id="ebaf9-115">La première étape consiste à créer le projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebaf9-116">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="ebaf9-117">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="ebaf9-117">To create the project</span></span>  
  
-   <span data-ttu-id="ebaf9-118">Créer un nouveau projet d’Application Windows Forms dans Visual Basic ou Visual c# nommé `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="ebaf9-119">Création des types de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="ebaf9-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="ebaf9-120">Une fois que vous avez ajouté un type de contrôle WPF au projet, vous pouvez l'héberger dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="ebaf9-121">Pour créer des types de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="ebaf9-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="ebaf9-122">Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="ebaf9-123">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="ebaf9-124">Pour plus d’informations, consultez [procédure pas à pas : création WPF de contenu dans les Windows Forms au moment du Design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="ebaf9-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="ebaf9-125">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="ebaf9-126">Pour plus d’informations, consultez [Comment : sélectionner et déplacer des éléments sur l’aire de conception](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="ebaf9-126">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="ebaf9-127">Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés `200`.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="ebaf9-128">Ajouter un <xref:System.Windows.Controls.Button?displayProperty=nameWithType> le contrôle à la <xref:System.Windows.Controls.UserControl> et définissez la valeur de la <xref:System.Windows.Controls.ContentControl.Content%2A> propriété **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="ebaf9-129">Ajoutez un deuxième <xref:System.Windows.Controls.Button?displayProperty=nameWithType> le contrôle à la <xref:System.Windows.Controls.UserControl> et définissez la valeur de la <xref:System.Windows.Controls.ContentControl.Content%2A> propriété **OK**.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="ebaf9-130">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="ebaf9-131">Application d'un style à un contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="ebaf9-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="ebaf9-132">Vous pouvez appliquer différents styles à un contrôle WPF pour modifier son apparence et son comportement.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="ebaf9-133">Pour appliquer un style à un contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="ebaf9-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="ebaf9-134">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="ebaf9-135">Dans le **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="ebaf9-136">Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="ebaf9-137">Dans le panneau des balises actives pour `elementHost1`, cliquez sur **modifier le contenu hébergé** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="ebaf9-138">`UserControl1` s'ouvre dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ebaf9-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="ebaf9-139">En mode XAML, insérez le code XAML suivant après la balise d'ouverture `<UserControl>`.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="ebaf9-140">Ce code XAML crée un dégradé avec une bordure de dégradé contrastée.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="ebaf9-141">Quand l'utilisateur clique sur le contrôle, les dégradés sont modifiés pour générer une apparence de bouton enfoncé.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="ebaf9-142">Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="ebaf9-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
```xaml  
<UserControl.Resources>  
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#FFF" Offset="0.0"/>  
        <GradientStop Color="#CCC" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#BBB" Offset="0.0"/>  
        <GradientStop Color="#EEE" Offset="0.1"/>  
        <GradientStop Color="#EEE" Offset="0.9"/>  
        <GradientStop Color="#FFF" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#CCC" Offset="0.0"/>  
        <GradientStop Color="#444" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#CCC" Offset="0.0"/>  
        <GradientStop Color="#444" Offset="1.0"/>  
    </LinearGradientBrush>  
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">  
        <GradientStop Color="#444" Offset="0.0"/>  
        <GradientStop Color="#888" Offset="1.0"/>  
    </LinearGradientBrush>  
  
    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>  
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>  
        <Setter Property="Template">  
            <Setter.Value>  
                <ControlTemplate TargetType="{x:Type Button}">  
                    <Grid x:Name="Grid">  
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>  
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>  
                    </Grid>  
                    <ControlTemplate.Triggers>  
                        <Trigger Property="IsPressed" Value="true">  
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>  
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>  
                        </Trigger>  
                    </ControlTemplate.Triggers>  
                </ControlTemplate>  
            </Setter.Value>  
        </Setter>  
    </Style>  
</UserControl.Resources>  
```  
  
1.  <span data-ttu-id="ebaf9-143">Appliquez le style `SimpleButton` défini à l'étape précédente au bouton Annuler en insérant le code XAML suivant dans la balise `<Button>` du bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="ebaf9-144">Votre déclaration de bouton ressemblera au code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="ebaf9-145">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="ebaf9-146">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="ebaf9-147">Le nouveau style est appliqué au contrôle de bouton.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="ebaf9-148">À partir de la **déboguer** menu, sélectionnez **démarrer le débogage** pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="ebaf9-149">Cliquez sur les boutons OK et Annuler et observez les différences.</span><span class="sxs-lookup"><span data-stu-id="ebaf9-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebaf9-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebaf9-150">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="ebaf9-151">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="ebaf9-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="ebaf9-152">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="ebaf9-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="ebaf9-153">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="ebaf9-153">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="ebaf9-154">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="ebaf9-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="ebaf9-155">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="ebaf9-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
