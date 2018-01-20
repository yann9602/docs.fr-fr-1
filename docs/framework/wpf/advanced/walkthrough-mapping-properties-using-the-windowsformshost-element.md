---
title: "Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaab6b7724a1e6145dfce3998ccf75904df01802
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="f4ae3-102">Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="f4ae3-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>
<span data-ttu-id="f4ae3-103">Cette procédure pas à pas vous montre comment utiliser le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> propriété à mapper [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés dans les propriétés correspondantes sur hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
 <span data-ttu-id="f4ae3-104">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="f4ae3-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="f4ae3-105">Création du projet.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="f4ae3-106">Définition de la disposition de l’application.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-106">Defining the application layout.</span></span>  
  
-   <span data-ttu-id="f4ae3-107">Définition d’un nouveau mappage de propriété.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-107">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="f4ae3-108">Suppression d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-108">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="f4ae3-109">Remplacement d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-109">Replacing a default property mapping.</span></span>  
  
-   <span data-ttu-id="f4ae3-110">Extension d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-110">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="f4ae3-111">Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [propriétés de mappage à l’aide de l’élément WindowsFormsHost, exemple](http://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="f4ae3-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](http://go.microsoft.com/fwlink/?LinkID=160019).</span></span>  
  
 <span data-ttu-id="f4ae3-112">Lorsque vous avez terminé, vous ne pourrez pas mapper [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés dans les propriétés correspondantes sur hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f4ae3-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f4ae3-113">Prerequisites</span></span>  
 <span data-ttu-id="f4ae3-114">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="f4ae3-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="f4ae3-115">.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f4ae3-116">Création du projet</span><span class="sxs-lookup"><span data-stu-id="f4ae3-116">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="f4ae3-117">Pour créer et configurer le projet</span><span class="sxs-lookup"><span data-stu-id="f4ae3-117">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="f4ae3-118">Créez un projet d’Application WPF nommé `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-118">Create a WPF Application project named `PropertyMappingWithWfhSample`.</span></span>  
  
2.  <span data-ttu-id="f4ae3-119">Dans l’Explorateur de solutions, ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-119">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="f4ae3-120">Dans l’Explorateur de solutions, ajoutez des références aux assemblys System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-120">In Solution Explorer, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="defining-the-application-layout"></a><span data-ttu-id="f4ae3-121">Définition de la disposition de l’application</span><span class="sxs-lookup"><span data-stu-id="f4ae3-121">Defining the Application Layout</span></span>  
 <span data-ttu-id="f4ae3-122">Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application utilise le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément pour héberger un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-122">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-define-the-application-layout"></a><span data-ttu-id="f4ae3-123">Pour définir la disposition de l’application</span><span class="sxs-lookup"><span data-stu-id="f4ae3-123">To define the application layout</span></span>  
  
1.  <span data-ttu-id="f4ae3-124">Ouvrez Window1.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4ae3-124">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="f4ae3-125">Remplacez le code existant par le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-125">Replace the existing code with the following code.</span></span>  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  <span data-ttu-id="f4ae3-126">Ouvrez Window1.xaml.cs dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-126">Open Window1.xaml.cs in the Code Editor.</span></span>  
  
4.  <span data-ttu-id="f4ae3-127">En haut du fichier, importez les espaces de noms suivants.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-127">At the top of the file, import the following namespaces.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="f4ae3-128">Définition d’un nouveau mappage de propriété</span><span class="sxs-lookup"><span data-stu-id="f4ae3-128">Defining a New Property Mapping</span></span>  
 <span data-ttu-id="f4ae3-129">Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément fournit des mappages de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-129">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="f4ae3-130">Vous ajoutez un nouveau mappage de propriété en appelant le <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> méthode sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="f4ae3-131">Pour définir un nouveau mappage de propriété</span><span class="sxs-lookup"><span data-stu-id="f4ae3-131">To define a new property mapping</span></span>  
  
-   <span data-ttu-id="f4ae3-132">Copiez le code suivant dans la définition de la `Window1` classe.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-132">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     <span data-ttu-id="f4ae3-133">Le `AddClipMapping` méthode ajoute un nouveau mappage pour le <xref:System.Windows.UIElement.Clip%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-133">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="f4ae3-134">Le `OnClipChange` méthode traduit le <xref:System.Windows.UIElement.Clip%2A> propriété le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-134">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="f4ae3-135">Le `Window1_SizeChanged` méthode gère la fenêtre <xref:System.Windows.FrameworkElement.SizeChanged> événement et la taille de la zone de découpage pour s’ajuster à la fenêtre d’application.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-135">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="f4ae3-136">Suppression d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="f4ae3-136">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="f4ae3-137">Supprimer un mappage de propriété par défaut en appelant le <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> méthode sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-137">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="f4ae3-138">Pour supprimer un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="f4ae3-138">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="f4ae3-139">Copiez le code suivant dans la définition de la `Window1` classe.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-139">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     <span data-ttu-id="f4ae3-140">Le `RemoveCursorMapping` méthode supprime le mappage par défaut pour le <xref:System.Windows.FrameworkElement.Cursor%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-140">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>  
  
## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="f4ae3-141">Remplacement d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="f4ae3-141">Replacing a Default Property Mapping</span></span>  
 <span data-ttu-id="f4ae3-142">Remplacer un mappage de propriété par défaut en supprimant le mappage par défaut et en appelant le <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> méthode sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-142">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="f4ae3-143">Pour remplacer un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="f4ae3-143">To replace a default property mapping</span></span>  
  
-   <span data-ttu-id="f4ae3-144">Copiez le code suivant dans la définition de la `Window1` classe.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-144">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     <span data-ttu-id="f4ae3-145">Le `ReplaceFlowDirectionMapping` méthode remplace le mappage par défaut pour le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-145">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>  
  
     <span data-ttu-id="f4ae3-146">Le `OnFlowDirectionChange` méthode traduit le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-146">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>  
  
     <span data-ttu-id="f4ae3-147">Le `cb_CheckedChanged` méthode gère le <xref:System.Windows.Forms.CheckBox.CheckedChanged> événement sur le <xref:System.Windows.Forms.CheckBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-147">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="f4ae3-148">Elle attribue le <xref:System.Windows.FrameworkElement.FlowDirection%2A> basée sur les propriétés de la valeur de la <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété</span><span class="sxs-lookup"><span data-stu-id="f4ae3-148">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="f4ae3-149">Extension d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="f4ae3-149">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="f4ae3-150">Vous pouvez utiliser un mappage de propriété par défaut et l’étendre avec votre propre mappage.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-150">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="f4ae3-151">Pour étendre un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="f4ae3-151">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="f4ae3-152">Copiez le code suivant dans la définition de la `Window1` classe.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-152">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     <span data-ttu-id="f4ae3-153">Le `ExtendBackgroundMapping` méthode ajoute un traducteur de propriété personnalisé à l’objet existant <xref:System.Windows.Controls.Control.Background%2A> mappage de propriété.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-153">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>  
  
     <span data-ttu-id="f4ae3-154">Le `OnBackgroundChange` méthode assigne une image spécifique du contrôle hébergé <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-154">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="f4ae3-155">Le `OnBackgroundChange` méthode est appelée une fois le mappage de propriété par défaut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-155">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="f4ae3-156">Initialisation de vos mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="f4ae3-156">Initializing Your Property Mappings</span></span>  
 <span data-ttu-id="f4ae3-157">Définissez vos mappages de propriété en appelant les méthodes décrites précédemment dans le <xref:System.Windows.FrameworkElement.Loaded> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-157">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="f4ae3-158">Pour initialiser vos mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="f4ae3-158">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="f4ae3-159">Copiez le code suivant dans la définition de la `Window1` classe.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-159">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     <span data-ttu-id="f4ae3-160">Le `WindowLoaded` méthode gère le <xref:System.Windows.FrameworkElement.Loaded> événement et exécute l’initialisation suivante.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-160">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="f4ae3-161">Crée un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-161">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>  
  
    -   <span data-ttu-id="f4ae3-162">Appelle les méthodes que vous avez définies précédemment dans la procédure pas à pas pour configurer les mappages de propriétés.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-162">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="f4ae3-163">Assigne les valeurs initiales aux propriétés mappées.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-163">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="f4ae3-164">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-164">Press F5 to build and run the application.</span></span> <span data-ttu-id="f4ae3-165">Cliquez sur la case à cocher pour voir l’effet de la <xref:System.Windows.FrameworkElement.FlowDirection%2A> mappage.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-165">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="f4ae3-166">Quand vous cliquez sur la case à cocher, la disposition inverse son orientation de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="f4ae3-166">When you click the check box, the layout reverses its left-right orientation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ae3-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4ae3-167">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="f4ae3-168">Mappage de propriétés Windows Forms et WPF</span><span class="sxs-lookup"><span data-stu-id="f4ae3-168">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="f4ae3-169">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="f4ae3-169">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="f4ae3-170">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="f4ae3-170">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
