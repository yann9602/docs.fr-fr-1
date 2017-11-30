---
title: "Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost"
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
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dae954012d15431d2019d3d9cbe61747a8646d4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="81177-102">Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost</span><span class="sxs-lookup"><span data-stu-id="81177-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>
<span data-ttu-id="81177-103">Cette procédure pas à pas vous montre comment utiliser le <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> propriété à mapper [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriétés dans les propriétés correspondantes sur hébergé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] élément.</span><span class="sxs-lookup"><span data-stu-id="81177-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>  
  
 <span data-ttu-id="81177-104">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="81177-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="81177-105">Création du projet.</span><span class="sxs-lookup"><span data-stu-id="81177-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="81177-106">Définition d’un nouveau mappage de propriété.</span><span class="sxs-lookup"><span data-stu-id="81177-106">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="81177-107">Suppression d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="81177-107">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="81177-108">Extension d’un mappage de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="81177-108">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="81177-109">Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [propriétés de mappage à l’aide de l’exemple de contrôle ElementHost](http://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="81177-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](http://go.microsoft.com/fwlink/?LinkID=160018).</span></span>  
  
 <span data-ttu-id="81177-110">Lorsque vous avez terminé, vous ne pourrez pas mapper [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aux propriétés correspondent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés sur un élément hébergé.</span><span class="sxs-lookup"><span data-stu-id="81177-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="81177-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="81177-111">Prerequisites</span></span>  
 <span data-ttu-id="81177-112">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="81177-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="81177-113">.</span><span class="sxs-lookup"><span data-stu-id="81177-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="81177-114">Création du projet</span><span class="sxs-lookup"><span data-stu-id="81177-114">Creating the Project</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="81177-115">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="81177-115">To create the project</span></span>  
  
1.  <span data-ttu-id="81177-116">Créer un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projet d’application nommé `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="81177-116">Create a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project named `PropertyMappingWithElementHost`.</span></span> <span data-ttu-id="81177-117">Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="81177-117">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="81177-118">Dans l’Explorateur de solutions, ajoutez des références à ce qui suit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblys.</span><span class="sxs-lookup"><span data-stu-id="81177-118">In Solution Explorer, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>  
  
    -   <span data-ttu-id="81177-119">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="81177-119">PresentationCore</span></span>  
  
    -   <span data-ttu-id="81177-120">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="81177-120">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="81177-121">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="81177-121">WindowsBase</span></span>  
  
    -   <span data-ttu-id="81177-122">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="81177-122">WindowsFormsIntegration</span></span>  
  
3.  <span data-ttu-id="81177-123">Copiez le code suivant en haut de la `Form1` fichier de code.</span><span class="sxs-lookup"><span data-stu-id="81177-123">Copy the following code into the top of the `Form1` code file.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="81177-124">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="81177-124">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="81177-125">Double-cliquez sur le formulaire pour ajouter un gestionnaire d’événements pour le <xref:System.Windows.Forms.Form.Load> événement.</span><span class="sxs-lookup"><span data-stu-id="81177-125">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
5.  <span data-ttu-id="81177-126">Revenez au Concepteur Windows Forms et ajoutez un gestionnaire d’événements du formulaire <xref:System.Windows.Forms.Control.Resize> événement.</span><span class="sxs-lookup"><span data-stu-id="81177-126">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="81177-127">Pour plus d’informations, consultez [Comment : créer des événements gestionnaires de l’aide du concepteur](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span><span class="sxs-lookup"><span data-stu-id="81177-127">For more information, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
6.  <span data-ttu-id="81177-128">Déclarez une <xref:System.Windows.Forms.Integration.ElementHost> champ la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="81177-128">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a><span data-ttu-id="81177-129">Définition de nouveaux mappages de propriété</span><span class="sxs-lookup"><span data-stu-id="81177-129">Defining New Property Mappings</span></span>  
 <span data-ttu-id="81177-130">Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle fournit des mappages de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="81177-130">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="81177-131">Vous ajoutez un nouveau mappage de propriété en appelant le <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> méthode sur le <xref:System.Windows.Forms.Integration.ElementHost> du contrôle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="81177-131">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-new-property-mappings"></a><span data-ttu-id="81177-132">Pour définir de nouveaux mappages de propriété</span><span class="sxs-lookup"><span data-stu-id="81177-132">To define new property mappings</span></span>  
  
1.  <span data-ttu-id="81177-133">Copiez le code suivant dans la définition de la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="81177-133">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     <span data-ttu-id="81177-134">Le `AddMarginMapping` méthode ajoute un nouveau mappage pour le <xref:System.Windows.Forms.Control.Margin%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="81177-134">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>  
  
     <span data-ttu-id="81177-135">Le `OnMarginChange` méthode traduit le <xref:System.Windows.Forms.Control.Margin%2A> propriété le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="81177-135">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>  
  
2.  <span data-ttu-id="81177-136">Copiez le code suivant dans la définition de la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="81177-136">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     <span data-ttu-id="81177-137">Le `AddRegionMapping` méthode ajoute un nouveau mappage pour le <xref:System.Windows.Forms.Control.Region%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="81177-137">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="81177-138">Le `OnRegionChange` méthode traduit le <xref:System.Windows.Forms.Control.Region%2A> propriété le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="81177-138">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="81177-139">Le `Form1_Resize` méthode gère du formulaire <xref:System.Windows.Forms.Control.Resize> événement et la taille de la zone de découpage pour s’ajuster à l’élément hébergé.</span><span class="sxs-lookup"><span data-stu-id="81177-139">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="81177-140">Suppression d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="81177-140">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="81177-141">Supprimer un mappage de propriété par défaut en appelant le <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> méthode sur le <xref:System.Windows.Forms.Integration.ElementHost> du contrôle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="81177-141">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="81177-142">Pour supprimer un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="81177-142">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="81177-143">Copiez le code suivant dans la définition de la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="81177-143">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     <span data-ttu-id="81177-144">Le `RemoveCursorMapping` méthode supprime le mappage par défaut pour le <xref:System.Windows.Forms.Control.Cursor%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="81177-144">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="81177-145">Extension d’un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="81177-145">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="81177-146">Vous pouvez utiliser un mappage de propriété par défaut et l’étendre avec votre propre mappage.</span><span class="sxs-lookup"><span data-stu-id="81177-146">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="81177-147">Pour étendre un mappage de propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="81177-147">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="81177-148">Copiez le code suivant dans la définition de la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="81177-148">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     <span data-ttu-id="81177-149">Le `ExtendBackColorMapping` méthode ajoute un traducteur de propriété personnalisé à l’objet existant <xref:System.Windows.Forms.Control.BackColor%2A> mappage de propriété.</span><span class="sxs-lookup"><span data-stu-id="81177-149">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>  
  
     <span data-ttu-id="81177-150">Le `OnBackColorChange` méthode assigne une image spécifique du contrôle hébergé <xref:System.Windows.Controls.Control.Background%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="81177-150">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="81177-151">Le `OnBackColorChange` méthode est appelée une fois le mappage de propriété par défaut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="81177-151">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="81177-152">Initialisation de vos mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="81177-152">Initializing Your Property Mappings</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="81177-153">Pour initialiser vos mappages de propriétés</span><span class="sxs-lookup"><span data-stu-id="81177-153">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="81177-154">Copiez le code suivant dans la définition de la `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="81177-154">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     <span data-ttu-id="81177-155">Le `Form1_Load` méthode gère le <xref:System.Windows.Forms.Form.Load> événement et exécute l’initialisation suivante.</span><span class="sxs-lookup"><span data-stu-id="81177-155">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="81177-156">Crée un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> élément.</span><span class="sxs-lookup"><span data-stu-id="81177-156">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>  
  
    -   <span data-ttu-id="81177-157">Appelle les méthodes que vous avez définies précédemment dans la procédure pas à pas pour configurer les mappages de propriétés.</span><span class="sxs-lookup"><span data-stu-id="81177-157">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="81177-158">Assigne les valeurs initiales aux propriétés mappées.</span><span class="sxs-lookup"><span data-stu-id="81177-158">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="81177-159">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="81177-159">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81177-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81177-160">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="81177-161">Mappage de propriétés Windows Forms et WPF</span><span class="sxs-lookup"><span data-stu-id="81177-161">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="81177-162">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="81177-162">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="81177-163">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81177-163">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
