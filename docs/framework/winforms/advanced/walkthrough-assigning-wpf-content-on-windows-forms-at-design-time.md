---
title: "Procédure pas à pas : assignation du contenu WPF sur les Windows Forms au moment du design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93ff6f39f4d8bcdd037d373f8bd26cbb3c32c125
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="d16b2-102">Procédure pas à pas : assignation du contenu WPF sur les Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="d16b2-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="d16b2-103">Cette procédure pas à pas montre comment sélectionner les types de contrôle WPF (Windows Presentation Foundation) que vous souhaitez afficher sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="d16b2-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="d16b2-104">Vous pouvez sélectionner tout type de contrôle WPF inclus dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="d16b2-104">You can select any WPF control types which are included in your project.</span></span>  
  
 <span data-ttu-id="d16b2-105">Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d16b2-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="d16b2-106">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="d16b2-106">Create the project.</span></span>  
  
-   <span data-ttu-id="d16b2-107">créer les types de contrôles WPF ;</span><span class="sxs-lookup"><span data-stu-id="d16b2-107">Create the WPF control types.</span></span>  
  
-   <span data-ttu-id="d16b2-108">sélectionner les contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="d16b2-108">Select WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d16b2-109">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="d16b2-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d16b2-110">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="d16b2-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d16b2-111">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d16b2-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d16b2-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="d16b2-112">Prerequisites</span></span>  
 <span data-ttu-id="d16b2-113">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="d16b2-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="d16b2-114">.</span><span class="sxs-lookup"><span data-stu-id="d16b2-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d16b2-115">Création du projet</span><span class="sxs-lookup"><span data-stu-id="d16b2-115">Creating the Project</span></span>  
 <span data-ttu-id="d16b2-116">La première étape consiste à créer le projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d16b2-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d16b2-117">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d16b2-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d16b2-118">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="d16b2-118">To create the project</span></span>  
  
-   <span data-ttu-id="d16b2-119">Créer un nouveau projet d’Application Windows Forms dans Visual Basic ou Visual c# nommé `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="d16b2-120">Création des types de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="d16b2-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="d16b2-121">Après avoir ajouté des types de contrôles WPF au projet, vous pouvez les héberger dans différents contrôles <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="d16b2-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="d16b2-122">Pour créer des types de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="d16b2-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="d16b2-123">Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.</span><span class="sxs-lookup"><span data-stu-id="d16b2-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="d16b2-124">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="d16b2-125">Pour plus d’informations, consultez [procédure pas à pas : création WPF de contenu dans les Windows Forms au moment du Design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="d16b2-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="d16b2-126">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d16b2-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="d16b2-127">Pour plus d’informations, consultez [Comment : sélectionner et déplacer des éléments sur l’aire de conception](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="d16b2-127">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="d16b2-128">Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés `200`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="d16b2-129">Ajouter un <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> le contrôle à la <xref:System.Windows.Controls.UserControl> et définissez la valeur de la <xref:System.Windows.Controls.TextBox.Text%2A> propriété **le contenu hébergé**.</span><span class="sxs-lookup"><span data-stu-id="d16b2-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="d16b2-130">Ajoutez un deuxième <xref:System.Windows.Controls.UserControl> WPF au projet.</span><span class="sxs-lookup"><span data-stu-id="d16b2-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="d16b2-131">Utilisez le nom par défaut pour le type de contrôle, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="d16b2-132">Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés `200`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="d16b2-133">Ajouter un <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> le contrôle à la <xref:System.Windows.Controls.UserControl> et définissez la valeur de la <xref:System.Windows.Controls.TextBox.Text%2A> propriété **contenu hébergé 2**.</span><span class="sxs-lookup"><span data-stu-id="d16b2-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="d16b2-134">**Remarque** en général, vous devez héberger du contenu WPF plus sophistiqué.</span><span class="sxs-lookup"><span data-stu-id="d16b2-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="d16b2-135">Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> est utilisé ici uniquement à titre d'illustration.</span><span class="sxs-lookup"><span data-stu-id="d16b2-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="d16b2-136">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="d16b2-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="d16b2-137">Sélection des contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="d16b2-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="d16b2-138">Vous pouvez assigner du contenu WPF différent à un contrôle <xref:System.Windows.Forms.Integration.ElementHost> qui héberge déjà du contenu.</span><span class="sxs-lookup"><span data-stu-id="d16b2-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="d16b2-139">Pour sélectionner des contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="d16b2-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="d16b2-140">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d16b2-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="d16b2-141">Dans le **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d16b2-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="d16b2-142">Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="d16b2-143">Dans le panneau des balises actives pour `elementHost1`, ouvrez le **sélectionner le contenu hébergé** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="d16b2-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="d16b2-144">Sélectionnez **UserControl2** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="d16b2-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="d16b2-145">Le contrôle `elementHost1` héberge maintenant une instance du type `UserControl2`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="d16b2-146">Dans le **propriétés** fenêtre, vérifiez que le <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> est définie sur **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="d16b2-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="d16b2-147">À partir de la **boîte à outils**, dans le **interopérabilité WPF** de groupe, faites glisser un <xref:System.Windows.Forms.Integration.ElementHost> contrôle vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="d16b2-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="d16b2-148">Le nom par défaut du nouveau contrôle est `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="d16b2-149">Dans le panneau des balises actives pour `elementHost2`, ouvrez le **sélectionner le contenu hébergé** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="d16b2-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="d16b2-150">Sélectionnez **UserControl1** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="d16b2-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="d16b2-151">Le contrôle `elementHost2` héberge maintenant une instance du type `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="d16b2-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d16b2-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d16b2-152">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="d16b2-153">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d16b2-153">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="d16b2-154">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="d16b2-154">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="d16b2-155">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="d16b2-155">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
