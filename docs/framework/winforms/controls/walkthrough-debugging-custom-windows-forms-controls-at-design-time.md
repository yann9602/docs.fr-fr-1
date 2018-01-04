---
title: "Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design"
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
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fd38f6246d44bd24753d9c86a5b0b08819d3db7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="f7a90-102">Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design</span><span class="sxs-lookup"><span data-stu-id="f7a90-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="f7a90-103">Lorsque vous créez un contrôle personnalisé, il est souvent s’avérer nécessaire de déboguer son comportement au moment du design.</span><span class="sxs-lookup"><span data-stu-id="f7a90-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="f7a90-104">Cela est particulièrement vrai si vous êtes en train de créer un concepteur personnalisé pour votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7a90-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="f7a90-105">Pour plus d’informations, consultez [procédure pas à pas : création d’un Windows Forms contrôle que prend parti des fonctionnalités Visual Studio au moment du Design](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="f7a90-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="f7a90-106">Vous pouvez déboguer vos contrôles personnalisés à l’aide de Visual Studio, comme vous le feriez d’autres classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7a90-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="f7a90-107">La différence est que vous allez déboguer une instance distincte de Visual Studio qui exécute le code de votre contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="f7a90-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="f7a90-108">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="f7a90-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="f7a90-109">Création d’un projet Windows Forms pour héberger votre contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="f7a90-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="f7a90-110">Création d’un projet de bibliothèque de contrôles</span><span class="sxs-lookup"><span data-stu-id="f7a90-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="f7a90-111">Ajout d’une propriété à votre contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="f7a90-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="f7a90-112">Ajout de votre contrôle personnalisé au formulaire hôte</span><span class="sxs-lookup"><span data-stu-id="f7a90-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="f7a90-113">Configuration du projet pour le débogage au moment du design</span><span class="sxs-lookup"><span data-stu-id="f7a90-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="f7a90-114">Débogage de votre contrôle personnalisé au moment du design</span><span class="sxs-lookup"><span data-stu-id="f7a90-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="f7a90-115">Lorsque vous avez terminé, vous devez comprendre les tâches nécessaires pour déboguer le comportement au moment du design d’un contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7a90-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7a90-116">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="f7a90-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f7a90-117">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="f7a90-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f7a90-118">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f7a90-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f7a90-119">Création du projet</span><span class="sxs-lookup"><span data-stu-id="f7a90-119">Creating the Project</span></span>  
 <span data-ttu-id="f7a90-120">La première étape consiste à créer le projet d’application.</span><span class="sxs-lookup"><span data-stu-id="f7a90-120">The first step is to create the application project.</span></span> <span data-ttu-id="f7a90-121">Vous utiliserez ce projet pour générer l’application qui héberge le contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7a90-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f7a90-122">Pour créer le projet</span><span class="sxs-lookup"><span data-stu-id="f7a90-122">To create the project</span></span>  
  
-   <span data-ttu-id="f7a90-123">Créez un projet d’Application Windows appelé « DebuggingExample ».</span><span class="sxs-lookup"><span data-stu-id="f7a90-123">Create a Windows Application project called "DebuggingExample".</span></span> <span data-ttu-id="f7a90-124">Pour plus d’informations, consultez l’article [Comment : créer un projet d’application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="f7a90-124">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="f7a90-125">Création d’un projet de bibliothèque de contrôles</span><span class="sxs-lookup"><span data-stu-id="f7a90-125">Creating a Control Library Project</span></span>  
 <span data-ttu-id="f7a90-126">L’étape suivante consiste à créer le projet de bibliothèque de contrôles et de configurer le contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7a90-126">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="f7a90-127">Pour créer le projet de bibliothèque de contrôle</span><span class="sxs-lookup"><span data-stu-id="f7a90-127">To create the control library project</span></span>  
  
1.  <span data-ttu-id="f7a90-128">Ajouter un **bibliothèque de contrôles Windows** projet à la solution.</span><span class="sxs-lookup"><span data-stu-id="f7a90-128">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="f7a90-129">Ajouter un nouveau **UserControl** élément au projet DebugControlLibrary.</span><span class="sxs-lookup"><span data-stu-id="f7a90-129">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="f7a90-130">Pour plus d’informations, consultez [NIB : Comment : ajouter de nouveaux éléments de projet](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span><span class="sxs-lookup"><span data-stu-id="f7a90-130">For details, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="f7a90-131">Nommez le nouveau fichier source une base « DebugControl ».</span><span class="sxs-lookup"><span data-stu-id="f7a90-131">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="f7a90-132">À l’aide de la **l’Explorateur de solutions**, supprimer le contrôle du projet par défaut en supprimant le fichier de code avec un nom de base «`UserControl1`».</span><span class="sxs-lookup"><span data-stu-id="f7a90-132">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="f7a90-133">Pour plus d’informations, consultez [NIB : Comment : exclure des éléments, de suppression et de suppression](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="f7a90-133">For details, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="f7a90-134">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="f7a90-134">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="f7a90-135">Point de contrôle</span><span class="sxs-lookup"><span data-stu-id="f7a90-135">Checkpoint</span></span>  
 <span data-ttu-id="f7a90-136">À ce stade, vous serez en mesure de voir votre contrôle personnalisé dans le **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="f7a90-136">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="f7a90-137">Pour vérifier votre progression</span><span class="sxs-lookup"><span data-stu-id="f7a90-137">To check your progress</span></span>  
  
-   <span data-ttu-id="f7a90-138">Recherchez le nouvel onglet appelé **Composants DebugControlLibrary** et cliquez sur pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="f7a90-138">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="f7a90-139">Quand il s’ouvre, vous verrez votre contrôle répertorié comme **DebugControl** avec l’icône par défaut à côté de lui.</span><span class="sxs-lookup"><span data-stu-id="f7a90-139">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="f7a90-140">Ajout d’une propriété à votre contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="f7a90-140">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="f7a90-141">Pour montrer que le code de votre contrôle personnalisé s’exécute au moment du design, vous ajoutez une propriété et définissez un point d’arrêt dans le code qui implémente la propriété.</span><span class="sxs-lookup"><span data-stu-id="f7a90-141">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="f7a90-142">Pour ajouter une propriété à votre contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="f7a90-142">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="f7a90-143">Ouvrez **DebugControl** dans les **éditeur de Code**.</span><span class="sxs-lookup"><span data-stu-id="f7a90-143">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="f7a90-144">Ajoutez le code suivant à la définition de classe :</span><span class="sxs-lookup"><span data-stu-id="f7a90-144">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="f7a90-145">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="f7a90-145">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="f7a90-146">Ajout de votre contrôle personnalisé au formulaire hôte</span><span class="sxs-lookup"><span data-stu-id="f7a90-146">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="f7a90-147">Pour déboguer le comportement au moment du design de votre contrôle personnalisé, vous devez placer une instance de la classe de contrôle personnalisé dans un formulaire de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="f7a90-147">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="f7a90-148">Pour ajouter votre contrôle personnalisé au formulaire hôte</span><span class="sxs-lookup"><span data-stu-id="f7a90-148">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="f7a90-149">Dans le projet « DebuggingExample », ouvrez Form1 dans le **Concepteur Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="f7a90-149">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="f7a90-150">Dans le **boîte à outils**, ouvrez le **Composants DebugControlLibrary** onglet et faites glisser un **DebugControl** instance sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="f7a90-150">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="f7a90-151">Rechercher les `DemoString` une propriété personnalisée dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="f7a90-151">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="f7a90-152">Notez que vous pouvez modifier sa valeur comme vous le feriez pour n’importe quelle autre propriété.</span><span class="sxs-lookup"><span data-stu-id="f7a90-152">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="f7a90-153">Notez également que lorsque la `DemoString` propriété est sélectionnée, la chaîne de description de la propriété apparaît en bas de la **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="f7a90-153">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f7a90-154">Configuration du projet pour le débogage au moment du Design</span><span class="sxs-lookup"><span data-stu-id="f7a90-154">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="f7a90-155">Pour déboguer le comportement au moment du design de votre contrôle personnalisé, vous allez déboguer une instance distincte de Visual Studio qui exécute le code de votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7a90-155">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f7a90-156">Pour configurer le projet pour le débogage au moment du design</span><span class="sxs-lookup"><span data-stu-id="f7a90-156">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="f7a90-157">Avec le bouton droit sur le **DebugControlLibrary** de projet dans le **l’Explorateur de solutions** et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f7a90-157">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f7a90-158">Dans le **DebugControlLibrary** feuille de propriétés, sélectionnez le **déboguer** onglet.</span><span class="sxs-lookup"><span data-stu-id="f7a90-158">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="f7a90-159">Dans le **Action de démarrage** section, sélectionnez **démarrer le programme externe**.</span><span class="sxs-lookup"><span data-stu-id="f7a90-159">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="f7a90-160">Vous pourrez déboguer une instance distincte de Visual Studio, cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) bouton pour rechercher l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7a90-160">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="f7a90-161">Le nom du fichier exécutable est **devenv.exe**, et si vous avez installé à l’emplacement par défaut, son chemin d’accès est %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span><span class="sxs-lookup"><span data-stu-id="f7a90-161">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="f7a90-162">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f7a90-162">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="f7a90-163">Avec le bouton droit le **DebugControlLibrary** de projet et sélectionnez **définir comme projet de démarrage** pour activer cette configuration de débogage.</span><span class="sxs-lookup"><span data-stu-id="f7a90-163">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="f7a90-164">Débogage de votre contrôle personnalisé au moment du Design</span><span class="sxs-lookup"><span data-stu-id="f7a90-164">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="f7a90-165">Vous êtes maintenant prêt à déboguer votre contrôle personnalisé lorsqu’elle s’exécute en mode Création.</span><span class="sxs-lookup"><span data-stu-id="f7a90-165">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="f7a90-166">Lorsque vous démarrez la session de débogage, une nouvelle instance de Visual Studio est créée, et vous allez l’utiliser pour charger la solution « DebuggingExample ».</span><span class="sxs-lookup"><span data-stu-id="f7a90-166">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="f7a90-167">Lorsque vous ouvrez Form1 dans le **le Concepteur de formulaires**, une instance de votre contrôle personnalisé est créée et commence à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="f7a90-167">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="f7a90-168">Pour déboguer votre contrôle personnalisé au moment du design</span><span class="sxs-lookup"><span data-stu-id="f7a90-168">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="f7a90-169">Ouvrir le **DebugControl** fichier source dans le **éditeur de Code** et placer un point d’arrêt sur la `Set` l’accesseur de la `DemoString` propriété.</span><span class="sxs-lookup"><span data-stu-id="f7a90-169">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="f7a90-170">Appuyez sur F5 pour démarrer la session de débogage.</span><span class="sxs-lookup"><span data-stu-id="f7a90-170">Press F5 to start the debugging session.</span></span> <span data-ttu-id="f7a90-171">Notez qu’une nouvelle instance de Visual Studio est créée.</span><span class="sxs-lookup"><span data-stu-id="f7a90-171">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="f7a90-172">Vous pouvez faire la distinction entre les instances de deux manières :</span><span class="sxs-lookup"><span data-stu-id="f7a90-172">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="f7a90-173">L’instance de débogage a le mot **en cours d’exécution** dans la barre de titre</span><span class="sxs-lookup"><span data-stu-id="f7a90-173">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="f7a90-174">L’instance de débogage a le **Démarrer** bouton sur son **déboguer** barre d’outils désactivé</span><span class="sxs-lookup"><span data-stu-id="f7a90-174">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="f7a90-175">Votre point d’arrêt est défini dans l’instance de débogage.</span><span class="sxs-lookup"><span data-stu-id="f7a90-175">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="f7a90-176">Dans la nouvelle instance de Visual Studio, ouvrez la solution « DebuggingExample ».</span><span class="sxs-lookup"><span data-stu-id="f7a90-176">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="f7a90-177">Vous pouvez rechercher facilement la solution en sélectionnant **projets récents** à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="f7a90-177">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="f7a90-178">Le fichier de solution « DebuggingExample.sln » apparaît comme le dernier fichier utilisé.</span><span class="sxs-lookup"><span data-stu-id="f7a90-178">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="f7a90-179">Ouvrez Form1 dans le **le Concepteur de formulaires** et sélectionnez le **DebugControl** contrôle.</span><span class="sxs-lookup"><span data-stu-id="f7a90-179">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="f7a90-180">Modifiez la valeur de la `DemoString` propriété.</span><span class="sxs-lookup"><span data-stu-id="f7a90-180">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="f7a90-181">Notez que lorsque vous validez la modification, l’instance de débogage de Visual Studio acquiert le focus et l’exécution s’arrête au point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="f7a90-181">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="f7a90-182">Vous pouvez la seule étape à l’accesseur de propriété comme votre serait tout autre code.</span><span class="sxs-lookup"><span data-stu-id="f7a90-182">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="f7a90-183">Lorsque vous avez terminé votre session de débogage, vous pouvez quitter en fermant l’instance hébergée de Visual Studio ou en cliquant sur le **arrêter le débogage** bouton dans l’instance de débogage.</span><span class="sxs-lookup"><span data-stu-id="f7a90-183">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f7a90-184">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f7a90-184">Next Steps</span></span>  
 <span data-ttu-id="f7a90-185">Maintenant que vous pouvez déboguer vos contrôles personnalisés au moment du design, il existe de nombreuses possibilités pour le développement d’interaction de votre contrôle avec l’IDE Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7a90-185">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="f7a90-186">Vous pouvez utiliser la <xref:System.ComponentModel.Component.DesignMode%2A> propriété de la <xref:System.ComponentModel.Component> classe pour écrire du code qui s’exécute uniquement au moment du design.</span><span class="sxs-lookup"><span data-stu-id="f7a90-186">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="f7a90-187">Pour plus d'informations, consultez <xref:System.ComponentModel.Component.DesignMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7a90-187">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="f7a90-188">Il existe plusieurs attributs que vous pouvez appliquer aux propriétés de votre contrôle pour manipuler l’interaction de votre contrôle personnalisé avec le concepteur.</span><span class="sxs-lookup"><span data-stu-id="f7a90-188">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="f7a90-189">Vous pouvez trouver ces attributs dans le <xref:System.ComponentModel?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f7a90-189">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="f7a90-190">Vous pouvez écrire un concepteur personnalisé pour votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f7a90-190">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="f7a90-191">Cela vous donne un contrôle complet sur l’expérience de conception à l’aide de l’infrastructure du concepteur extensible exposée par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7a90-191">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="f7a90-192">Pour plus d’informations, consultez [procédure pas à pas : création d’un Windows Forms contrôle que prend parti des fonctionnalités Visual Studio au moment du Design](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span><span class="sxs-lookup"><span data-stu-id="f7a90-192">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a90-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7a90-193">See Also</span></span>  
 [<span data-ttu-id="f7a90-194">Procédure pas à pas : création d’un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f7a90-194">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="f7a90-195">Comment : accéder aux Services au moment du Design</span><span class="sxs-lookup"><span data-stu-id="f7a90-195">How to: Access Design-Time Services</span></span>](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="f7a90-196">Comment : accéder à la prise en charge au moment du Design dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7a90-196">How to: Access Design-Time Support in Windows Forms</span></span>](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
