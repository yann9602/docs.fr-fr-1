---
title: "Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cfbe9957fa8d18f839ae656ca721c4ee88475a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="6e83c-102">Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="6e83c-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="6e83c-103">Cette rubrique montre comment créer un contrôle Windows Presentation Foundation (WPF) pour une utilisation dans vos applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6e83c-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>  
  
 <span data-ttu-id="6e83c-104">Au cours de cette procédure pas à pas, vous allez exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="6e83c-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="6e83c-105">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="6e83c-105">Create the project.</span></span>  
  
-   <span data-ttu-id="6e83c-106">créer un projet WPF ;</span><span class="sxs-lookup"><span data-stu-id="6e83c-106">Create a new WPF control.</span></span>  
  
-   <span data-ttu-id="6e83c-107">ajouter le nouveau contrôle WPF à un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="6e83c-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="6e83c-108">Le contrôle WPF est hébergé dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="6e83c-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e83c-109">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="6e83c-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6e83c-110">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="6e83c-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6e83c-111">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="6e83c-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6e83c-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="6e83c-112">Prerequisites</span></span>  
 <span data-ttu-id="6e83c-113">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="6e83c-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="6e83c-114">.</span><span class="sxs-lookup"><span data-stu-id="6e83c-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="6e83c-115">Création du projet</span><span class="sxs-lookup"><span data-stu-id="6e83c-115">Creating the Project</span></span>  
 <span data-ttu-id="6e83c-116">La première étape consiste à créer le projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6e83c-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e83c-117">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6e83c-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="6e83c-118">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="6e83c-118">To create the project</span></span>  
  
-   <span data-ttu-id="6e83c-119">Créer un nouveau projet d’Application Windows Forms dans Visual Basic ou Visual c# nommé `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="6e83c-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `HostingWpf`.</span></span>  
  
## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="6e83c-120">Création d'un contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="6e83c-120">Creating a New WPF Control</span></span>  
 <span data-ttu-id="6e83c-121">La création d'un contrôle WPF et son ajout à votre projet sont des tâches aussi simples que l'ajout de tout autre élément à votre projet.</span><span class="sxs-lookup"><span data-stu-id="6e83c-121">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="6e83c-122">Le Concepteur Windows Forms fonctionne avec un type particulier de contrôle nommé *contrôle composite*, ou *contrôle utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="6e83c-122">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="6e83c-123">Pour plus d'informations sur les contrôles utilisateur WPF, consultez <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="6e83c-123">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e83c-124">Le type <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> pour WPF est distinct du type de contrôle utilisateur fourni par Windows Forms, également nommé <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e83c-124">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>  
  
#### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="6e83c-125">Pour créer un contrôle WPF</span><span class="sxs-lookup"><span data-stu-id="6e83c-125">To create a new WPF control</span></span>  
  
1.  <span data-ttu-id="6e83c-126">Dans **l’Explorateur de solutions**, ajoutez un nouveau **bibliothèque de contrôles utilisateur WPF** projet à la solution.</span><span class="sxs-lookup"><span data-stu-id="6e83c-126">In **Solution Explorer**, add a new **WPF User Control Library** project to the solution.</span></span> <span data-ttu-id="6e83c-127">Utilisez le nom par défaut pour la bibliothèque de contrôles, `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="6e83c-127">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="6e83c-128">Le nom du contrôle par défaut est `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="6e83c-128">The default control name is `UserControl1.xaml`.</span></span>  
  
     <span data-ttu-id="6e83c-129">L'ajout du nouveau contrôle a les effets suivants.</span><span class="sxs-lookup"><span data-stu-id="6e83c-129">Adding the new control has the following effects.</span></span>  
  
    -   <span data-ttu-id="6e83c-130">Le fichier UserControl1.xaml est ajouté.</span><span class="sxs-lookup"><span data-stu-id="6e83c-130">File UserControl1.xaml is added.</span></span>  
  
    -   <span data-ttu-id="6e83c-131">Le fichier UserControl1.xaml.cs ou UserControl1.xaml.vb est ajouté.</span><span class="sxs-lookup"><span data-stu-id="6e83c-131">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="6e83c-132">Ce fichier contient le code-behind pour les gestionnaires d'événements et autre implémentation.</span><span class="sxs-lookup"><span data-stu-id="6e83c-132">This file contains the code-behind for event handlers and other implementation.</span></span>  
  
    -   <span data-ttu-id="6e83c-133">Les références aux assemblys WPF sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="6e83c-133">References to WPF assemblies are added.</span></span>  
  
    -   <span data-ttu-id="6e83c-134">Le fichier UserControl1.xaml s'ouvre dans le [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e83c-134">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="6e83c-135">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="6e83c-135">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="6e83c-136">Pour plus d’informations, consultez [Comment : sélectionner et déplacer des éléments sur l’aire de conception](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="6e83c-136">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="6e83c-137">Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés `200`.</span><span class="sxs-lookup"><span data-stu-id="6e83c-137">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="6e83c-138">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> contrôle sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="6e83c-138">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>  
  
5.  <span data-ttu-id="6e83c-139">Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.Controls.TextBox.Text%2A> propriété **le contenu hébergé**.</span><span class="sxs-lookup"><span data-stu-id="6e83c-139">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e83c-140">En général, vous devez héberger du contenu WPF plus sophistiqué.</span><span class="sxs-lookup"><span data-stu-id="6e83c-140">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="6e83c-141">Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> est utilisé ici uniquement à titre d'illustration.</span><span class="sxs-lookup"><span data-stu-id="6e83c-141">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
6.  <span data-ttu-id="6e83c-142">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="6e83c-142">Build the project.</span></span>  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="6e83c-143">Ajout d'un contrôle WPF à un Windows Form</span><span class="sxs-lookup"><span data-stu-id="6e83c-143">Adding a WPF Control to a Windows Form</span></span>  
 <span data-ttu-id="6e83c-144">Votre nouveau contrôle WPF est prêt à être utilisé sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="6e83c-144">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="6e83c-145">Windows Forms utilise le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour héberger le contenu WPF</span><span class="sxs-lookup"><span data-stu-id="6e83c-145">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content</span></span>  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="6e83c-146">Pour ajouter un contrôle WPF à un Windows Form</span><span class="sxs-lookup"><span data-stu-id="6e83c-146">To add a WPF control to a Windows Form</span></span>  
  
1.  <span data-ttu-id="6e83c-147">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6e83c-147">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="6e83c-148">Dans le **boîte à outils**, l’onglet **contrôles utilisateur WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="6e83c-148">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>  
  
3.  <span data-ttu-id="6e83c-149">Faites glisser une instance de `UserControl1` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="6e83c-149">Drag an instance of `UserControl1` onto the form.</span></span>  
  
    -   <span data-ttu-id="6e83c-150">Un contrôle <xref:System.Windows.Forms.Integration.ElementHost> est créé automatiquement sur le formulaire pour héberger le contrôle WPF.</span><span class="sxs-lookup"><span data-stu-id="6e83c-150">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>  
  
    -   <span data-ttu-id="6e83c-151">Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle est nommé `elementHost1` et dans le **propriétés** fenêtre, vous pouvez voir son <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> est définie sur **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="6e83c-151">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>  
  
    -   <span data-ttu-id="6e83c-152">des références aux assemblys WPF sont ajoutées au projet.</span><span class="sxs-lookup"><span data-stu-id="6e83c-152">References to WPF assemblies are added to the project.</span></span>  
  
    -   <span data-ttu-id="6e83c-153">Le contrôle `elementHost1` a un panneau de Smart Tags qui affiche les options d'hébergement disponibles.</span><span class="sxs-lookup"><span data-stu-id="6e83c-153">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>  
  
4.  <span data-ttu-id="6e83c-154">Dans le **tâches ElementHost** panneau des balises actives, sélectionnez **ancrer dans le conteneur parent**.</span><span class="sxs-lookup"><span data-stu-id="6e83c-154">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>  
  
5.  <span data-ttu-id="6e83c-155">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="6e83c-155">Press F5 to build and run the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6e83c-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6e83c-156">Next Steps</span></span>  
 <span data-ttu-id="6e83c-157">Windows Forms et WPF sont des technologies différentes, mais elles sont conçues pour interagir étroitement.</span><span class="sxs-lookup"><span data-stu-id="6e83c-157">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="6e83c-158">Pour fournir une apparence et un comportement enrichis dans vos applications, essayez ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="6e83c-158">To provide richer appearance and behavior in your applications, try the following.</span></span>  
  
-   <span data-ttu-id="6e83c-159">Hébergez un contrôle Windows Forms dans une page WPF.</span><span class="sxs-lookup"><span data-stu-id="6e83c-159">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="6e83c-160">Pour plus d’informations, consultez [procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="6e83c-160">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
-   <span data-ttu-id="6e83c-161">Appliquez des styles visuels Windows Forms à votre contenu WPF.</span><span class="sxs-lookup"><span data-stu-id="6e83c-161">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="6e83c-162">Pour plus d’informations, consultez [Guide pratique pour activer des styles visuels dans une application hybride](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="6e83c-162">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>  
  
-   <span data-ttu-id="6e83c-163">Modifiez le style de votre contenu WPF.</span><span class="sxs-lookup"><span data-stu-id="6e83c-163">Change the style of your WPF content.</span></span> <span data-ttu-id="6e83c-164">Pour plus d’informations, consultez [procédure pas à pas : conception de styles de contenu WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="6e83c-164">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e83c-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e83c-165">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="6e83c-166">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="6e83c-166">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="6e83c-167">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="6e83c-167">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="6e83c-168">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="6e83c-168">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
