---
title: "Procédure pas à pas : localisation d'une application hybride"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f9bb7588ef1f6962a5cd55196154ac7f666d53b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="195ed-102">Procédure pas à pas : localisation d'une application hybride</span><span class="sxs-lookup"><span data-stu-id="195ed-102">Walkthrough: Localizing a Hybrid Application</span></span>
<span data-ttu-id="195ed-103">Cette procédure pas à pas vous indique comment localiser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] éléments dans un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-application hybride.</span><span class="sxs-lookup"><span data-stu-id="195ed-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>  
  
 <span data-ttu-id="195ed-104">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="195ed-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="195ed-105">Création de la [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projet hôte.</span><span class="sxs-lookup"><span data-stu-id="195ed-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>  
  
-   <span data-ttu-id="195ed-106">Ajout de contenu localisable</span><span class="sxs-lookup"><span data-stu-id="195ed-106">Adding localizable content.</span></span>  
  
-   <span data-ttu-id="195ed-107">Activation de la localisation</span><span class="sxs-lookup"><span data-stu-id="195ed-107">Enabling localization.</span></span>  
  
-   <span data-ttu-id="195ed-108">Assignation d’identificateurs de ressource</span><span class="sxs-lookup"><span data-stu-id="195ed-108">Assigning resource identifiers.</span></span>  
  
-   <span data-ttu-id="195ed-109">Utilisation de l’outil LocBaml pour produire un assembly satellite</span><span class="sxs-lookup"><span data-stu-id="195ed-109">Using the LocBaml tool to produce a satellite assembly.</span></span>  
  
 <span data-ttu-id="195ed-110">Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [localisation d’une Application hybride, exemple](http://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="195ed-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](http://go.microsoft.com/fwlink/?LinkID=160015).</span></span>  
  
 <span data-ttu-id="195ed-111">Quand vous aurez terminé, vous disposerez d’une application hybride localisée.</span><span class="sxs-lookup"><span data-stu-id="195ed-111">When you are finished, you will have a localized hybrid application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="195ed-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="195ed-112">Prerequisites</span></span>  
 <span data-ttu-id="195ed-113">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="195ed-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="195ed-114">.</span><span class="sxs-lookup"><span data-stu-id="195ed-114">.</span></span>  
  
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="195ed-115">Création du projet hôte Windows Forms</span><span class="sxs-lookup"><span data-stu-id="195ed-115">Creating the Windows Forms Host Project</span></span>  
 <span data-ttu-id="195ed-116">La première étape consiste à créer le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application du projet et ajouter un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] élément avec du contenu qui vous serez localiser.</span><span class="sxs-lookup"><span data-stu-id="195ed-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="195ed-117">Pour créer le projet hôte</span><span class="sxs-lookup"><span data-stu-id="195ed-117">To create the host project</span></span>  
  
1.  <span data-ttu-id="195ed-118">Créez un projet d’Application WPF nommé `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="195ed-118">Create a WPF Application project named `LocalizingWpfInWf`.</span></span> <span data-ttu-id="195ed-119">Pour plus d’informations, consultez [Comment : créer un projet d’application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="195ed-119">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="195ed-120">Ajouter un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> élément appelé `SimpleControl` au projet.</span><span class="sxs-lookup"><span data-stu-id="195ed-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>  
  
3.  <span data-ttu-id="195ed-121">Utilisez le <xref:System.Windows.Forms.Integration.ElementHost> contrôle se place un `SimpleControl` élément sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="195ed-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="195ed-122">Pour plus d’informations, consultez [procédure pas à pas : hébergement d’un contrôle Composite 3D de WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="195ed-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>  
  
## <a name="adding-localizable-content"></a><span data-ttu-id="195ed-123">Ajout de contenu localisable</span><span class="sxs-lookup"><span data-stu-id="195ed-123">Adding Localizable Content</span></span>  
 <span data-ttu-id="195ed-124">Ensuite, vous allez ajouter un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label, contrôle et définir le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu de l’élément à une chaîne localisable.</span><span class="sxs-lookup"><span data-stu-id="195ed-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>  
  
#### <a name="to-add-localizable-content"></a><span data-ttu-id="195ed-125">Pour ajouter du contenu localisable</span><span class="sxs-lookup"><span data-stu-id="195ed-125">To add localizable content</span></span>  
  
1.  <span data-ttu-id="195ed-126">Dans l’Explorateur de solutions, double-cliquez sur **SimpleControl.XAML le** pour l’ouvrir dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="195ed-126">In Solution Explorer, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="195ed-127">Définir le contenu de la <xref:System.Windows.Controls.Button> contrôler à l’aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="195ed-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  <span data-ttu-id="195ed-128">Dans l’Explorateur de solutions, double-cliquez sur **Form1** pour l’ouvrir dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="195ed-128">In Solution Explorer, double-click **Form1** to open it in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="195ed-129">Ouvrez la boîte à outils et double-cliquez sur **étiquette** pour ajouter un contrôle d’étiquette au formulaire.</span><span class="sxs-lookup"><span data-stu-id="195ed-129">Open the Toolbox and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="195ed-130">Affectez à sa propriété <xref:System.Windows.Forms.Control.Text%2A> la valeur `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="195ed-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>  
  
5.  <span data-ttu-id="195ed-131">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="195ed-131">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="195ed-132">Les deux le `SimpleControl` élément et le contrôle label affichent le texte **« Hello »**.</span><span class="sxs-lookup"><span data-stu-id="195ed-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>  
  
## <a name="enabling-localization"></a><span data-ttu-id="195ed-133">Activation de la localisation</span><span class="sxs-lookup"><span data-stu-id="195ed-133">Enabling Localization</span></span>  
 <span data-ttu-id="195ed-134">Le Concepteur Windows Forms comprend des paramètres permettant d’activer la localisation dans un assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="195ed-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>  
  
#### <a name="to-enable-localization"></a><span data-ttu-id="195ed-135">Pour activer la localisation</span><span class="sxs-lookup"><span data-stu-id="195ed-135">To enable localization</span></span>  
  
1.  <span data-ttu-id="195ed-136">Dans l’Explorateur de solutions, double-cliquez sur **Form1.cs** pour l’ouvrir dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="195ed-136">In Solution Explorer, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="195ed-137">Dans la fenêtre Propriétés, définissez la valeur du formulaire **Localizable** propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="195ed-137">In the Properties window, set the value of the form's **Localizable** property to `true`.</span></span>  
  
3.  <span data-ttu-id="195ed-138">Dans la fenêtre Propriétés, définissez la valeur de la **langage** propriété **Espagnol (Espagne)**.</span><span class="sxs-lookup"><span data-stu-id="195ed-138">In the Properties window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>  
  
4.  <span data-ttu-id="195ed-139">Dans le Concepteur Windows Forms, sélectionnez le contrôle d’étiquette.</span><span class="sxs-lookup"><span data-stu-id="195ed-139">In the Windows Forms Designer, select the label control.</span></span>  
  
5.  <span data-ttu-id="195ed-140">Dans la fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.Control.Text%2A> propriété `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="195ed-140">In the Properties window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>  
  
     <span data-ttu-id="195ed-141">Un nouveau fichier de ressources nommé Form1.es-ES.resx est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="195ed-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>  
  
6.  <span data-ttu-id="195ed-142">Dans l’Explorateur de solutions, cliquez sur **Form1.cs** et cliquez sur **afficher le Code** pour l’ouvrir dans l’éditeur de Code.</span><span class="sxs-lookup"><span data-stu-id="195ed-142">In Solution Explorer, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>  
  
7.  <span data-ttu-id="195ed-143">Copiez le code suivant dans le `Form1` constructeur, précédant l’appel à `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="195ed-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  <span data-ttu-id="195ed-144">Dans l’Explorateur de solutions, cliquez sur **LocalizingWpfInWf** et cliquez sur **décharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="195ed-144">In Solution Explorer, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>  
  
     <span data-ttu-id="195ed-145">Le nom du projet est étiqueté **(non disponible)**.</span><span class="sxs-lookup"><span data-stu-id="195ed-145">The project name is labeled **(unavailable)**.</span></span>  
  
9. <span data-ttu-id="195ed-146">Avec le bouton droit **LocalizingWpfInWf**, puis cliquez sur **Modifier LocalizingWpfInWf.csproj**.</span><span class="sxs-lookup"><span data-stu-id="195ed-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>  
  
     <span data-ttu-id="195ed-147">Le fichier projet s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="195ed-147">The project file opens in the Code Editor.</span></span>  
  
10. <span data-ttu-id="195ed-148">Copiez la ligne suivante dans la première `PropertyGroup` dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="195ed-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. <span data-ttu-id="195ed-149">Enregistrez, puis fermez le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="195ed-149">Save the project file and close it.</span></span>  
  
12. <span data-ttu-id="195ed-150">Dans l’Explorateur de solutions, cliquez sur **LocalizingWpfInWf** et cliquez sur **recharger le projet**.</span><span class="sxs-lookup"><span data-stu-id="195ed-150">In Solution Explorer, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>  
  
## <a name="assigning-resource-identifiers"></a><span data-ttu-id="195ed-151">Assignation d’identificateurs de ressource</span><span class="sxs-lookup"><span data-stu-id="195ed-151">Assigning Resource Identifiers</span></span>  
 <span data-ttu-id="195ed-152">Vous pouvez mapper votre contenu localisable à des assemblys de ressources en utilisant des identificateurs de ressource.</span><span class="sxs-lookup"><span data-stu-id="195ed-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="195ed-153">L’application MsBuild.exe assigne automatiquement des identificateurs de ressource lorsque vous spécifiez la `updateuid` option.</span><span class="sxs-lookup"><span data-stu-id="195ed-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>  
  
#### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="195ed-154">Pour assigner des identificateurs de ressource</span><span class="sxs-lookup"><span data-stu-id="195ed-154">To assign resource identifiers</span></span>  
  
1.  <span data-ttu-id="195ed-155">Dans le Menu Démarrer, ouvrez le [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="195ed-155">From the Start Menu, open the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] Command Prompt.</span></span>  
  
2.  <span data-ttu-id="195ed-156">Utilisez la commande suivante pour assigner des identificateurs de ressource à votre contenu localisable.</span><span class="sxs-lookup"><span data-stu-id="195ed-156">Use the following command to assign resource identifiers to your localizable content.</span></span>  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  <span data-ttu-id="195ed-157">Dans l’Explorateur de solutions, double-cliquez sur **SimpleControl.XAML le** pour l’ouvrir dans l’éditeur de Code.</span><span class="sxs-lookup"><span data-stu-id="195ed-157">In Solution Explorer, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="195ed-158">Vous verrez que le `msbuild` commande a ajouté le `Uid` à tous les éléments d’attribut.</span><span class="sxs-lookup"><span data-stu-id="195ed-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="195ed-159">Cela facilite la localisation par l’assignation des identificateurs de ressource.</span><span class="sxs-lookup"><span data-stu-id="195ed-159">This facilitates localization through the assignment of resource identifiers.</span></span>  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  <span data-ttu-id="195ed-160">Appuyez sur F6 pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="195ed-160">Press F6 to build the solution.</span></span>  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="195ed-161">Utilisation de LocBaml pour produire un assembly satellite</span><span class="sxs-lookup"><span data-stu-id="195ed-161">Using LocBaml to Produce a Satellite Assembly</span></span>  
 <span data-ttu-id="195ed-162">Votre contenu localisé est stocké dans une ressource uniquement *assembly satellite*.</span><span class="sxs-lookup"><span data-stu-id="195ed-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="195ed-163">Utilisez l’outil de ligne de commande LocBaml.exe pour produire un assembly localisé pour votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu.</span><span class="sxs-lookup"><span data-stu-id="195ed-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  
  
#### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="195ed-164">Pour produire un assembly satellite</span><span class="sxs-lookup"><span data-stu-id="195ed-164">To produce a satellite assembly</span></span>  
  
1.  <span data-ttu-id="195ed-165">Copiez LocBaml.exe dans le dossier obj\Debug de votre projet.</span><span class="sxs-lookup"><span data-stu-id="195ed-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="195ed-166">Pour plus d’informations, consultez [localiser une Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="195ed-166">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>  
  
2.  <span data-ttu-id="195ed-167">Dans la fenêtre d’invite de commandes, utilisez la commande suivante pour extraire les chaînes de ressources dans un fichier temporaire.</span><span class="sxs-lookup"><span data-stu-id="195ed-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  <span data-ttu-id="195ed-168">Ouvrez le fichier temp.csv avec [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ou un autre éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="195ed-168">Open the temp.csv file with [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] or another text editor.</span></span> <span data-ttu-id="195ed-169">Remplacez la chaîne `"Hello"` avec sa traduction en espagnol, `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="195ed-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>  
  
4.  <span data-ttu-id="195ed-170">Enregistrez le fichier temp.csv.</span><span class="sxs-lookup"><span data-stu-id="195ed-170">Save the temp.csv file.</span></span>  
  
5.  <span data-ttu-id="195ed-171">Utilisez la commande suivante pour générer le fichier de ressources localisé.</span><span class="sxs-lookup"><span data-stu-id="195ed-171">Use the following command to generate the localized resource file.</span></span>  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     <span data-ttu-id="195ed-172">Le fichier LocalizingWpfInWf.g.es-ES.resources est créé dans le dossier obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="195ed-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>  
  
6.  <span data-ttu-id="195ed-173">Utilisez la commande suivante pour générer l’assembly satellite localisé.</span><span class="sxs-lookup"><span data-stu-id="195ed-173">Use the following command to build the localized satellite assembly.</span></span>  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     <span data-ttu-id="195ed-174">Le fichier LocalizingWpfInWf.resources.dll est créé dans le dossier obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="195ed-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>  
  
7.  <span data-ttu-id="195ed-175">Copiez le fichier LocalizingWpfInWf.resources.dll dans le dossier du projet bin\Debug\es-ES.</span><span class="sxs-lookup"><span data-stu-id="195ed-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="195ed-176">Remplacez le fichier existant.</span><span class="sxs-lookup"><span data-stu-id="195ed-176">Replace the existing file.</span></span>  
  
8.  <span data-ttu-id="195ed-177">Exécutez LocalizingWpfInWf.exe, qui se trouve dans le dossier bin\Debug de votre projet.</span><span class="sxs-lookup"><span data-stu-id="195ed-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="195ed-178">Ne regénérez pas l’application, car cela aura pour effet de remplacer l’assembly satellite.</span><span class="sxs-lookup"><span data-stu-id="195ed-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>  
  
     <span data-ttu-id="195ed-179">L’application affiche les chaînes localisées au lieu des chaînes en anglais.</span><span class="sxs-lookup"><span data-stu-id="195ed-179">The application shows the localized strings instead of the English strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195ed-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="195ed-180">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="195ed-181">Localiser une application</span><span class="sxs-lookup"><span data-stu-id="195ed-181">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [<span data-ttu-id="195ed-182">Procédure pas à pas : Localisation de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="195ed-182">Walkthrough: Localizing Windows Forms</span></span>](http://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [<span data-ttu-id="195ed-183">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="195ed-183">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
