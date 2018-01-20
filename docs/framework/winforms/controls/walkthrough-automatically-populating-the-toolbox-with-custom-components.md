---
title: "Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b60d4ee7908a5ed9dcb3393132ba7d0bd0a6cb5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a><span data-ttu-id="04dcc-102">Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="04dcc-102">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>
<span data-ttu-id="04dcc-103">Si vos composants sont définis par un projet dans la solution actuellement ouverte, ils apparaissent automatiquement dans le **boîte à outils**, sans aucune action requise par vous.</span><span class="sxs-lookup"><span data-stu-id="04dcc-103">If your components are defined by a project in the currently open solution, they will automatically appear in the **Toolbox**, with no action required by you.</span></span> <span data-ttu-id="04dcc-104">Vous pouvez également remplir manuellement la **boîte à outils** avec vos composants personnalisés à l’aide de la [choisir de boîte de dialogue des éléments de boîte à outils (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), mais la **boîte à outils** tient compte des éléments dans de votre solution génération avec toutes les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="04dcc-104">You can also manually populate the **Toolbox** with your custom components by using the [Choose Toolbox Items Dialog Box (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), but the **Toolbox** takes account of items in your solution's build outputs with all the following characteristics:</span></span>  
  
-   <span data-ttu-id="04dcc-105">Implémente <xref:System.ComponentModel.IComponent>;</span><span class="sxs-lookup"><span data-stu-id="04dcc-105">Implements <xref:System.ComponentModel.IComponent>;</span></span>  
  
-   <span data-ttu-id="04dcc-106">N’a pas <xref:System.ComponentModel.ToolboxItemAttribute> la valeur `false`;</span><span class="sxs-lookup"><span data-stu-id="04dcc-106">Does not have <xref:System.ComponentModel.ToolboxItemAttribute> set to `false`;</span></span>  
  
-   <span data-ttu-id="04dcc-107">N’a pas <xref:System.ComponentModel.DesignTimeVisibleAttribute> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="04dcc-107">Does not have <xref:System.ComponentModel.DesignTimeVisibleAttribute> set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04dcc-108">Le **boîte à outils** ne suit pas les chaînes de référence, il n’affichera pas les éléments qui ne sont pas générés par un projet dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="04dcc-108">The **Toolbox** does not follow reference chains, so it will not display items that are not built by a project in your solution.</span></span>  
  
 <span data-ttu-id="04dcc-109">Cette procédure pas à pas montre comment un composant personnalisé apparaît automatiquement dans le **boîte à outils** une fois que le composant est créé.</span><span class="sxs-lookup"><span data-stu-id="04dcc-109">This walkthrough demonstrates how a custom component automatically appears in the **Toolbox** once the component is built.</span></span> <span data-ttu-id="04dcc-110">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="04dcc-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="04dcc-111">Création d’un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="04dcc-111">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="04dcc-112">Création d’un composant personnalisé.</span><span class="sxs-lookup"><span data-stu-id="04dcc-112">Creating a custom component.</span></span>  
  
-   <span data-ttu-id="04dcc-113">Création d’une instance d’un composant personnalisé.</span><span class="sxs-lookup"><span data-stu-id="04dcc-113">Creating an instance of a custom component.</span></span>  
  
-   <span data-ttu-id="04dcc-114">Déchargement et le rechargement d’un composant personnalisé.</span><span class="sxs-lookup"><span data-stu-id="04dcc-114">Unloading and reloading a custom component.</span></span>  
  
 <span data-ttu-id="04dcc-115">Lorsque vous avez terminé, vous verrez que le **boîte à outils** est remplie avec un composant que vous avez créés.</span><span class="sxs-lookup"><span data-stu-id="04dcc-115">When you are finished, you will see that the **Toolbox** is populated with a component that you have created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04dcc-116">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="04dcc-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="04dcc-117">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="04dcc-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="04dcc-118">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="04dcc-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="04dcc-119">Création du projet</span><span class="sxs-lookup"><span data-stu-id="04dcc-119">Creating the Project</span></span>  
 <span data-ttu-id="04dcc-120">La première étape consiste à créer le projet et à configurer le formulaire.</span><span class="sxs-lookup"><span data-stu-id="04dcc-120">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="04dcc-121">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="04dcc-121">To create the project</span></span>  
  
1.  <span data-ttu-id="04dcc-122">Créez un projet d’application Windows appelé `ToolboxExample`.</span><span class="sxs-lookup"><span data-stu-id="04dcc-122">Create a Windows-based application project called `ToolboxExample`.</span></span>  
  
     <span data-ttu-id="04dcc-123">Pour plus d’informations, consultez [Comment : créer un projet d’application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="04dcc-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="04dcc-124">Ajoutez un nouveau composant au projet.</span><span class="sxs-lookup"><span data-stu-id="04dcc-124">Add a new component to the project.</span></span> <span data-ttu-id="04dcc-125">Appelez-le `DemoComponent`.</span><span class="sxs-lookup"><span data-stu-id="04dcc-125">Call it `DemoComponent`.</span></span>  
  
     <span data-ttu-id="04dcc-126">Pour plus d’informations, consultez [NIB : Comment : ajouter de nouveaux éléments de projet](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="04dcc-126">For more information, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span>  
  
3.  <span data-ttu-id="04dcc-127">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="04dcc-127">Build the project.</span></span>  
  
4.  <span data-ttu-id="04dcc-128">À partir de la **outils** menu, cliquez sur le **Options** élément.</span><span class="sxs-lookup"><span data-stu-id="04dcc-128">From the **Tools** menu, click the **Options** item.</span></span> <span data-ttu-id="04dcc-129">Cliquez sur **général** sous le **Concepteur Windows Forms** d’élément et vérifiez que le **AutoToolboxPopulate a** option est définie sur **True**.</span><span class="sxs-lookup"><span data-stu-id="04dcc-129">Click **General** under the **Windows Forms Designer** item and ensure that the **AutoToolboxPopulate** option is set to **True**.</span></span>  
  
## <a name="creating-an-instance-of-a-custom-component"></a><span data-ttu-id="04dcc-130">Création d’une Instance d’un composant personnalisé</span><span class="sxs-lookup"><span data-stu-id="04dcc-130">Creating an Instance of a Custom Component</span></span>  
 <span data-ttu-id="04dcc-131">L’étape suivante consiste à créer une instance du composant personnalisé sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="04dcc-131">The next step is to create an instance of the custom component on the form.</span></span> <span data-ttu-id="04dcc-132">Étant donné que la **boîte à outils** automatiquement des comptes pour le nouveau composant, c’est aussi simple que la création de tout autre composant ou contrôle.</span><span class="sxs-lookup"><span data-stu-id="04dcc-132">Because the **Toolbox** automatically accounts for the new component, this is as easy as creating any other component or control.</span></span>  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a><span data-ttu-id="04dcc-133">Pour créer une instance d’un composant personnalisé</span><span class="sxs-lookup"><span data-stu-id="04dcc-133">To create an instance of a custom component</span></span>  
  
1.  <span data-ttu-id="04dcc-134">Ouvrez le formulaire du projet dans le **Concepteur Forms**.</span><span class="sxs-lookup"><span data-stu-id="04dcc-134">Open the project's form in the **Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="04dcc-135">Dans le **boîte à outils**, cliquez sur le nouvel onglet appelé **Composants ToolboxExample**.</span><span class="sxs-lookup"><span data-stu-id="04dcc-135">In the **Toolbox**, click the new tab called **ToolboxExample Components**.</span></span>  
  
     <span data-ttu-id="04dcc-136">Une fois que vous cliquez sur l’onglet, vous verrez **DemoComponent**.</span><span class="sxs-lookup"><span data-stu-id="04dcc-136">Once you click the tab, you will see **DemoComponent**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04dcc-137">Pour des raisons de performances, les composants dans la zone et rempli automatiquement de la **boîte à outils** n’affichent pas de bitmaps personnalisées et le <xref:System.Drawing.ToolboxBitmapAttribute> n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="04dcc-137">For performance reasons, components in the auto-populated area of the **Toolbox** do not display custom bitmaps, and the <xref:System.Drawing.ToolboxBitmapAttribute> is not supported.</span></span> <span data-ttu-id="04dcc-138">Pour afficher une icône pour un composant personnalisé dans le **boîte à outils**, utilisez le **choisir des éléments de boîte à outils** boîte de dialogue pour charger votre composant.</span><span class="sxs-lookup"><span data-stu-id="04dcc-138">To display an icon for a custom component in the **Toolbox**, use the **Choose Toolbox Items** dialog box to load your component.</span></span>  
  
3.  <span data-ttu-id="04dcc-139">Faites glisser votre composant sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="04dcc-139">Drag your component onto your form.</span></span>  
  
     <span data-ttu-id="04dcc-140">Une instance du composant est créée et ajoutée à la **barre d’état du composant**.</span><span class="sxs-lookup"><span data-stu-id="04dcc-140">An instance of the component is created and added to the **Component Tray**.</span></span>  
  
## <a name="unloading-and-reloading-a-custom-component"></a><span data-ttu-id="04dcc-141">Décharger et recharger un composant personnalisé</span><span class="sxs-lookup"><span data-stu-id="04dcc-141">Unloading and Reloading a Custom Component</span></span>  
 <span data-ttu-id="04dcc-142">Le **boîte à outils** compte des composants dans chaque chargé de projet, et lorsqu’un projet est déchargé, elle supprime les références aux composants du projet.</span><span class="sxs-lookup"><span data-stu-id="04dcc-142">The **Toolbox** takes account of the components in each loaded project, and when a project is unloaded, it removes references to the project's components.</span></span>  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a><span data-ttu-id="04dcc-143">Pour tester l’effet sur la boîte à outils de décharger et recharger des composants</span><span class="sxs-lookup"><span data-stu-id="04dcc-143">To experiment with the effect on the Toolbox of unloading and reloading components</span></span>  
  
1.  <span data-ttu-id="04dcc-144">Décharger le projet à partir de la solution.</span><span class="sxs-lookup"><span data-stu-id="04dcc-144">Unload the project from the solution.</span></span>  
  
     <span data-ttu-id="04dcc-145">Pour plus d’informations sur le déchargement de projets, consultez [NIB : Comment : décharger et recharger des projets](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span><span class="sxs-lookup"><span data-stu-id="04dcc-145">For more information about unloading projects, see [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b).</span></span> <span data-ttu-id="04dcc-146">Si vous êtes invité à enregistrer, choisissez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="04dcc-146">If you are prompted to save, choose **Yes**.</span></span>  
  
2.  <span data-ttu-id="04dcc-147">Ajouter un nouveau **Application Windows** projet à la solution.</span><span class="sxs-lookup"><span data-stu-id="04dcc-147">Add a new **Windows Application** project to the solution.</span></span> <span data-ttu-id="04dcc-148">Ouvrez le formulaire dans le **concepteur**.</span><span class="sxs-lookup"><span data-stu-id="04dcc-148">Open the form in the **Designer**.</span></span>  
  
     <span data-ttu-id="04dcc-149">Le **Composants ToolboxExample** onglet dans le projet précédent est désormais disparu.</span><span class="sxs-lookup"><span data-stu-id="04dcc-149">The **ToolboxExample Components** tab from the previous project is now gone.</span></span>  
  
3.  <span data-ttu-id="04dcc-150">Recharger la `ToolboxExample` projet.</span><span class="sxs-lookup"><span data-stu-id="04dcc-150">Reload the `ToolboxExample` project.</span></span>  
  
     <span data-ttu-id="04dcc-151">Le **Composants ToolboxExample** onglet maintenant s’affiche de nouveau.</span><span class="sxs-lookup"><span data-stu-id="04dcc-151">The **ToolboxExample Components** tab now reappears.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="04dcc-152">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="04dcc-152">Next Steps</span></span>  
 <span data-ttu-id="04dcc-153">Cette procédure pas à pas montre que la **boîte à outils** tient compte des composants d’un projet, mais la **boîte à outils** tient également compte des contrôles.</span><span class="sxs-lookup"><span data-stu-id="04dcc-153">This walkthrough demonstrates that the **Toolbox** takes account of a project's components, but the **Toolbox** is also takes account of controls.</span></span> <span data-ttu-id="04dcc-154">Faites des essais avec vos propres contrôles personnalisés en ajoutant et supprimant des projets de contrôles à partir de votre solution.</span><span class="sxs-lookup"><span data-stu-id="04dcc-154">Experiment with your own custom controls by adding and removing control projects from your solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04dcc-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04dcc-155">See Also</span></span>  
 [<span data-ttu-id="04dcc-156">Général, Concepteur Windows Forms, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="04dcc-156">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="04dcc-157">Comment : manipuler des onglets de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="04dcc-157">How to: Manipulate Toolbox Tabs</span></span>](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [<span data-ttu-id="04dcc-158">Choisir des éléments de boîte à outils, boîte de dialogue (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="04dcc-158">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="04dcc-159">Placement de contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04dcc-159">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
