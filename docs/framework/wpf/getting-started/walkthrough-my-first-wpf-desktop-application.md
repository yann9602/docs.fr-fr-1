---
title: "Procédure pas à pas : Ma première application de bureau WPF"
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
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9818231a68f5c2ac2a6852f27e4876baa9728e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="0f6cb-102">Procédure pas à pas : Ma première application de bureau WPF</span><span class="sxs-lookup"><span data-stu-id="0f6cb-102">Walkthrough: My first WPF desktop application</span></span>
<span data-ttu-id="0f6cb-103">Cette procédure pas à pas fournit une introduction au développement d’un [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application qui inclut les éléments qui sont communes à la plupart des [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications : [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage, code-behind, définitions d’application, contrôles, disposition, liaison de données et styles.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-103">This walkthrough provides an introduction to the development of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application that includes the elements that are common to most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> 
  
 <span data-ttu-id="0f6cb-104">Cette procédure pas à pas vous guide dans le développement d’une simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application en procédant comme suit.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-104">This walkthrough guides you through the development of a simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application using the following steps.</span></span> 
  
-   <span data-ttu-id="0f6cb-105">Définition [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour concevoir l’apparence de l’application [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f6cb-105">Defining [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to design the appearance of the application's [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="0f6cb-106">Écriture de code pour générer le comportement de l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-106">Writing code to build the application's behavior.</span></span> 
  
-   <span data-ttu-id="0f6cb-107">Création d’une définition d’application pour gérer l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-107">Creating an application definition to manage the application.</span></span> 
  
-   <span data-ttu-id="0f6cb-108">Ajout de contrôles et la création de la disposition pour composer l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f6cb-108">Adding controls and creating the layout to compose the application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="0f6cb-109">Création de styles pour créer une apparence cohérente tout au long d’une application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f6cb-109">Creating styles to create a consistent appearance throughout an application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="0f6cb-110">Liaison de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à des données pour remplir le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à partir des données et de conserver les données et [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronisé.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-110">Binding the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to data to both populate the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] from data and keep the data and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronized.</span></span> 
  
 <span data-ttu-id="0f6cb-111">À la fin de la procédure pas à pas, vous aurez créé un autonome [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] qui permet aux utilisateurs de consulter les notes de frais pour certaines personnes.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-111">By the end of the walkthrough, you will have built a standalone [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="0f6cb-112">L’application sera composée de plusieurs [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages qui sont hébergées dans une fenêtre de style navigateur.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-112">The application will be composed of several [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages that are hosted in a browser-style window.</span></span> 
  
 <span data-ttu-id="0f6cb-113">L’exemple de code qui est utilisé pour générer cette procédure pas à pas est disponible pour les deux [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] et [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] à [Introduction à la génération d’Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-113">The sample code that is used to build this walkthrough is available for both [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] and [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] at  [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="0f6cb-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0f6cb-114">Prerequisites</span></span>  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="0f6cb-115"> ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="0f6cb-115"> or later</span></span>

<span data-ttu-id="0f6cb-116">Pour plus d’informations sur l’installation de la dernière version de Visual Studio, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>
  
## <a name="creating-the-application-project"></a><span data-ttu-id="0f6cb-117">Création du projet d’application</span><span class="sxs-lookup"><span data-stu-id="0f6cb-117">Creating the application project</span></span>  
 <span data-ttu-id="0f6cb-118">Dans cette section, vous allez créer l’infrastructure d’application, qui inclut une définition d’application, deux pages et une image.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-118">In this section, you create the application infrastructure, which includes an application definition, two pages, and an image.</span></span> 
  
1. <span data-ttu-id="0f6cb-119">Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `ExpenseIt`.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-119">Create a new WPF Application project in Visual Basic or Visual C# named `ExpenseIt`.</span></span> <span data-ttu-id="0f6cb-120">Pour plus d'informations, consultez [Guide pratique pour créer un projet d'application WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-120">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="0f6cb-121">Cette procédure pas à pas utilise le <xref:System.Windows.Controls.DataGrid> contrôle qui est disponible dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-121">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4.</span></span> <span data-ttu-id="0f6cb-122">Être sûr que votre projet cible le .NET Framework 4 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-122">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="0f6cb-123">Pour plus d’informations, consultez[Comment : cibler une Version du .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-123">For more information, see[How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
2. <span data-ttu-id="0f6cb-124">Ouvrez Application.xaml (Visual Basic) ou App.xaml (C#).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-124">Open Application.xaml (Visual Basic) or App.xaml (C#).</span></span> 
  
     <span data-ttu-id="0f6cb-125">Cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier définit un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application et toutes les ressources de l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-125">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file defines a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application and any application resources.</span></span> <span data-ttu-id="0f6cb-126">Vous utilisez également ce fichier pour spécifier le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui s’affiche automatiquement lorsque l’application démarre ; dans ce cas, MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-126">You also use this file to specify the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that automatically shows when the application starts; in this case, MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="0f6cb-127">Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-127">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     <span data-ttu-id="0f6cb-128">Ou à cela en C# :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-128">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. <span data-ttu-id="0f6cb-129">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-129">Open MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="0f6cb-130">Cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est la fenêtre principale de votre application et affiche le contenu créé dans les pages.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-130">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="0f6cb-131">La <xref:System.Windows.Window> classe définit les propriétés d’une fenêtre, telles que son titre, la taille ou icône et gère les événements, tels que la fermeture ou le masquage.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-131">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span> 
  
4. <span data-ttu-id="0f6cb-132">Modifier la <xref:System.Windows.Window> élément à un <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-132">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="0f6cb-133">Cette application accèdera à différents contenus en fonction de l’interaction de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-133">This application will navigate to different content depending on the user interaction.</span></span> <span data-ttu-id="0f6cb-134">Par conséquent, le principal <xref:System.Windows.Window> doit être remplacé par un <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-134">Therefore, the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="0f6cb-135"><xref:System.Windows.Navigation.NavigationWindow>hérite de toutes les propriétés de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-135"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="0f6cb-136">Le <xref:System.Windows.Navigation.NavigationWindow> élément dans le fichier XAML crée une instance de la <xref:System.Windows.Navigation.NavigationWindow> classe.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-136">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="0f6cb-137">Pour plus d’informations, consultez [Vue d’ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-137">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span> 
  
5. <span data-ttu-id="0f6cb-138">Modifiez les propriétés suivantes sur le <xref:System.Windows.Navigation.NavigationWindow> élément :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-138">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>  
  
    -   <span data-ttu-id="0f6cb-139">Définir le <xref:System.Windows.Window.Title%2A> propriété « ExpenseIt ».</span><span class="sxs-lookup"><span data-stu-id="0f6cb-139">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span> 
  
    -   <span data-ttu-id="0f6cb-140">Définir le <xref:System.Windows.FrameworkElement.Width%2A> propriété 500 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-140">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span> 
  
    -   <span data-ttu-id="0f6cb-141">Définir le <xref:System.Windows.FrameworkElement.Height%2A> propriété à 350 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-141">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span> 
  
    -   <span data-ttu-id="0f6cb-142">Supprimer le <xref:System.Windows.Controls.Grid> éléments entre les <xref:System.Windows.Navigation.NavigationWindow> balises.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-142">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span> 
  
     <span data-ttu-id="0f6cb-143">Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-143">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     <span data-ttu-id="0f6cb-144">Ou à cela en C# :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-144">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. <span data-ttu-id="0f6cb-145">Ouvrez MainWindow.xaml.vb ou MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-145">Open MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span> 
  
     <span data-ttu-id="0f6cb-146">Ce fichier est un fichier code-behind qui contient le code permettant de gérer les événements déclarés dans MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-146">This file is a code-behind file that contains code to handle the events declared in MainWindow.xaml.</span></span> <span data-ttu-id="0f6cb-147">Ce fichier contient une classe partielle pour la fenêtre définie en XAML.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-147">This file contains a partial class for the window defined in XAML.</span></span> 
  
7. <span data-ttu-id="0f6cb-148">Si vous utilisez c#, modifiez le `MainWindow` classe à dériver de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-148">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="0f6cb-149">En Visual Basic, cela se produit automatiquement quand vous modifiez la fenêtre en XAML.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-149">In Visual Basic, this happens automatically when you change the window in XAML.</span></span> 
  
     <span data-ttu-id="0f6cb-150">Votre code doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-150">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a><span data-ttu-id="0f6cb-151">Ajout de fichiers à l’application</span><span class="sxs-lookup"><span data-stu-id="0f6cb-151">Adding files to the application</span></span>  
 <span data-ttu-id="0f6cb-152">Dans cette section, vous allez ajouter deux pages et une image à l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-152">In this section, you add two pages and an image to the application.</span></span> 
  
1. <span data-ttu-id="0f6cb-153">Ajouter une nouvelle Page (WPF) au projet nommé `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-153">Add a new Page (WPF) to the project named `ExpenseItHome.xaml`.</span></span> <span data-ttu-id="0f6cb-154">Pour plus d’informations, consultez [Comment : ajouter de nouveaux éléments à un projet WPF](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-154">For more information, see [How to: Add New Items to a WPF Project](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span></span> 
  
     <span data-ttu-id="0f6cb-155">Cette page est la première page qui s’affiche au lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-155">This page is the first page that is displayed when the application is launched.</span></span> <span data-ttu-id="0f6cb-156">Elle affiche une liste dans laquelle un utilisateur peut sélectionner une personne pour en afficher les notes de frais.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-156">It will show a list of people from which a user can select a person to show an expense report for.</span></span> 
  
2. <span data-ttu-id="0f6cb-157">Ouvrez ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-157">Open ExpenseItHome.xaml.</span></span> 
  
3. <span data-ttu-id="0f6cb-158">Définir le <xref:System.Windows.Controls.Page.Title%2A> à « ExpenseIt - Home ».</span><span class="sxs-lookup"><span data-stu-id="0f6cb-158">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span> 
  
     <span data-ttu-id="0f6cb-159">Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-159">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     <span data-ttu-id="0f6cb-160">Ou à cela en C# :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-160">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. <span data-ttu-id="0f6cb-161">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-161">Open MainWindow.xaml.</span></span> 
  
5. <span data-ttu-id="0f6cb-162">Définir le <xref:System.Windows.Navigation.NavigationWindow.Source%2A> propriété sur le <xref:System.Windows.Navigation.NavigationWindow> à « ExpenseItHome.xaml ».</span><span class="sxs-lookup"><span data-stu-id="0f6cb-162">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span> 
  
     <span data-ttu-id="0f6cb-163">ExpenseItHome.xaml est alors la première page ouverte au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-163">This sets ExpenseItHome.xaml to be the first page opened when the application starts.</span></span> <span data-ttu-id="0f6cb-164">Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-164">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     <span data-ttu-id="0f6cb-165">Ou à cela en C# :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-165">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. <span data-ttu-id="0f6cb-166">Ajouter une nouvelle Page (WPF) au projet nommé `ExpenseReportPage.xaml`.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-166">Add a new Page (WPF) to the project named `ExpenseReportPage.xaml`.</span></span> 
  
     <span data-ttu-id="0f6cb-167">Cette page affiche la note de frais de la personne sélectionnée sur ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-167">This page will show the expense report for the person that is selected on ExpenseItHome.xaml.</span></span> 
  
7. <span data-ttu-id="0f6cb-168">Ouvrez ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-168">Open ExpenseReportPage.xaml.</span></span> 
  
8. <span data-ttu-id="0f6cb-169">Définir le <xref:System.Windows.Controls.Page.Title%2A> à « ExpenseIt - View Expense ».</span><span class="sxs-lookup"><span data-stu-id="0f6cb-169">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span> 
  
     <span data-ttu-id="0f6cb-170">Votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit ressembler à ceci en Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-170">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     <span data-ttu-id="0f6cb-171">Ou à cela en C# :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-171">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. <span data-ttu-id="0f6cb-172">Ouvrez ExpenseItHome.xaml.vb et ExpenseReportPage.xaml.vb, ou ExpenseItHome.xaml.cs et ExpenseReportPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-172">Open ExpenseItHome.xaml.vb and ExpenseReportPage.xaml.vb, or ExpenseItHome.xaml.cs and ExpenseReportPage.xaml.cs.</span></span> 
  
     <span data-ttu-id="0f6cb-173">Lorsque vous créez un nouveau fichier Page, Visual Studio crée automatiquement un fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-173">When you create a new Page file, Visual Studio automatically creates a code behind file.</span></span> <span data-ttu-id="0f6cb-174">Ces fichiers code-behind gèrent la logique pour répondre à une saisie de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-174">These code-behind files handle the logic for responding to user input.</span></span> 
  
     <span data-ttu-id="0f6cb-175">Votre code doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-175">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. <span data-ttu-id="0f6cb-176">Ajoutez au projet une image nommée watermark.png.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-176">Add an image named watermark.png to the project.</span></span> <span data-ttu-id="0f6cb-177">Vous pouvez soit créer votre propre image, soit copier le fichier à partir de l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-177">You can either create your own image, or copy the file from the sample code.</span></span> <span data-ttu-id="0f6cb-178">Pour plus d’informations, consultez [NIB : Comment : ajouter des éléments existants à un projet](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-178">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span> 

## <a name="building-and-running-the-application"></a><span data-ttu-id="0f6cb-179">Générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="0f6cb-179">Building and running the application</span></span>  
 <span data-ttu-id="0f6cb-180">Dans cette section, vous allez générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-180">In this section, you build and run the application.</span></span> 
  
1. <span data-ttu-id="0f6cb-181">Générer et exécuter l’application en appuyant sur F5 ou sélectionnez **démarrer le débogage** à partir de la **déboguer** menu.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-181">Build and run the application by pressing F5 or select **Start Debugging** from the **Debug** menu.</span></span> 
  
     <span data-ttu-id="0f6cb-182">L’illustration suivante montre l’application avec le <xref:System.Windows.Navigation.NavigationWindow> boutons.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-182">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons.</span></span> 
  
     <span data-ttu-id="0f6cb-183">![Exemple de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span><span class="sxs-lookup"><span data-stu-id="0f6cb-183">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span></span>  
  
2. <span data-ttu-id="0f6cb-184">Fermez l’application pour revenir à [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f6cb-184">Close the application to return to [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> 
  
## <a name="creating-the-layout"></a><span data-ttu-id="0f6cb-185">Création de la disposition</span><span class="sxs-lookup"><span data-stu-id="0f6cb-185">Creating the layout</span></span>  
 <span data-ttu-id="0f6cb-186">Mise en page offre placer de manière ordonnée [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments et gère également la taille et la position de ces éléments lorsqu’un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est redimensionné.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-186">Layout provides an ordered way to place [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements, and also manages the size and position of those elements when a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is resized.</span></span> <span data-ttu-id="0f6cb-187">En règle générale, vous allez créer une disposition avec l’un des contrôles de disposition suivants :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-187">You typically create a layout with one of the following layout controls:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="0f6cb-188">Chacun de ces contrôles de disposition prend en charge un type spécial de disposition pour ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-188">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="0f6cb-189">Les pages ExpenseIt peuvent être redimensionnées et chaque page comporte des éléments organisés horizontalement et verticalement en même temps que d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-189">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="0f6cb-190">Par conséquent, le <xref:System.Windows.Controls.Grid> est l’élément de disposition idéal pour l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-190">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="0f6cb-191">Pour plus d’informations sur <xref:System.Windows.Controls.Panel> éléments, consultez [vue d’ensemble des panneaux](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-191">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="0f6cb-192">Pour plus d’informations sur la mise en page, consultez [disposition](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-192">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span> 
  
 <span data-ttu-id="0f6cb-193">Dans la section, vous créez une seule colonne de table avec trois lignes et une marge de 10 pixels en ajoutant des définitions de colonne et de ligne à la <xref:System.Windows.Controls.Grid> dans ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-193">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in ExpenseItHome.xaml.</span></span> 
  
1. <span data-ttu-id="0f6cb-194">Ouvrez ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-194">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="0f6cb-195">Définir le <xref:System.Windows.FrameworkElement.Margin%2A> propriété sur le <xref:System.Windows.Controls.Grid> élément à la valeur « 10,0,10,10 » qui correspond aux marges gauche, haut, droite et bas.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-195">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10" which corresponds to left, top, right and bottom margins.</span></span> 
  
3. <span data-ttu-id="0f6cb-196">Ajoutez le code suivant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] entre les <xref:System.Windows.Controls.Grid> balises pour créer les définitions de ligne et de colonne.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-196">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions.</span></span> 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <span data-ttu-id="0f6cb-197">Le <xref:System.Windows.Controls.RowDefinition.Height%2A> de deux lignes est définie sur <xref:System.Windows.GridLength.Auto%2A> sur le contenu dans les lignes de base de ce qui signifie que les lignes seront redimensionnées.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-197">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A> which means that the rows will be sized base on the content in the rows.</span></span> <span data-ttu-id="0f6cb-198">La valeur par défaut <xref:System.Windows.Controls.RowDefinition.Height%2A> est <xref:System.Windows.GridUnitType.Star> dimensionnement, ce qui signifie que la ligne sera une proportion pondérée de l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-198">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row will be a weighted proportion of the available space.</span></span> <span data-ttu-id="0f6cb-199">Par exemple, si deux lignes ont une hauteur de « * », elles auront chacune une hauteur représentant la moitié de l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-199">For example if two rows each have a height of "*", they will each have a height that is half of the available space.</span></span>  
  
     <span data-ttu-id="0f6cb-200">Votre <xref:System.Windows.Controls.Grid> doit maintenant ressembler au code XAML suivant :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-200">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a><span data-ttu-id="0f6cb-201">Ajout de contrôles</span><span class="sxs-lookup"><span data-stu-id="0f6cb-201">Adding controls</span></span>  
 <span data-ttu-id="0f6cb-202">Dans cette section, la page d’accueil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est mis à jour pour afficher une liste des personnes que les utilisateurs peuvent sélectionner pour afficher la note de frais pour la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-202">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated to show a list of people that users can select from to show the expense report for a selected person.</span></span> <span data-ttu-id="0f6cb-203">Les contrôles sont des objets d’interface utilisateur qui permettent aux utilisateurs d’interagir avec votre application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-203">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="0f6cb-204">Pour plus d’informations, consultez [Contrôles](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-204">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span> 
  
 <span data-ttu-id="0f6cb-205">Pour créer ce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], les éléments suivants sont ajoutés à ExpenseItHome.xaml :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-205">To create this [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], the following elements are added to ExpenseItHome.xaml:</span></span>  
  
-   <span data-ttu-id="0f6cb-206"><xref:System.Windows.Controls.ListBox>(pour la liste des personnes).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-206"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span> 
  
-   <span data-ttu-id="0f6cb-207"><xref:System.Windows.Controls.Label>(pour l’en-tête de liste).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-207"><xref:System.Windows.Controls.Label> (for the list header).</span></span> 
  
-   <span data-ttu-id="0f6cb-208"><xref:System.Windows.Controls.Button>(pour cliquez pour afficher la note de frais pour la personne qui est sélectionnée dans la liste).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-208"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span> 
  
 <span data-ttu-id="0f6cb-209">Chaque contrôle est placé dans une ligne de la <xref:System.Windows.Controls.Grid> en définissant le <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> propriété jointe.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-209">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="0f6cb-210">Pour plus d’informations sur les propriétés jointes, consultez [joint la vue d’ensemble des propriétés](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-210">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span> 
  
1. <span data-ttu-id="0f6cb-211">Ouvrez ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-211">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="0f6cb-212">Ajoutez le code suivant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] entre les <xref:System.Windows.Controls.Grid> balises.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-212">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. <span data-ttu-id="0f6cb-213">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-213">Build and run the application.</span></span> 
  
 <span data-ttu-id="0f6cb-214">L’illustration suivante montre les contrôles créés par le code XAML dans cette section.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-214">The following illustration shows the controls that are created by the XAML in this section.</span></span> 
  
 <span data-ttu-id="0f6cb-215">![Exemple de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span><span class="sxs-lookup"><span data-stu-id="0f6cb-215">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span></span>  
  
## <a name="adding-an-image-and-a-title"></a><span data-ttu-id="0f6cb-216">Ajout d’une image et un titre</span><span class="sxs-lookup"><span data-stu-id="0f6cb-216">Adding an image and a title</span></span>  
 <span data-ttu-id="0f6cb-217">Dans cette section, la page d’accueil [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est mis à jour avec une image et un titre de page.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-217">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated with an image and a page title.</span></span> 
  
1. <span data-ttu-id="0f6cb-218">Ouvrez ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-218">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="0f6cb-219">Ajouter une colonne à la <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> fixe <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de 230 pixels.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-219">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels.</span></span> 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. <span data-ttu-id="0f6cb-220">Ajouter une autre ligne pour le <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-220">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span></span> 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. <span data-ttu-id="0f6cb-221">Déplacer les contrôles vers la deuxième colonne en définissant <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> sur 1.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-221">Move the controls to the second column by setting <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> to 1.</span></span> <span data-ttu-id="0f6cb-222">Déplacez chaque contrôle d’une ligne, vers le bas en augmentant la <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> par 1.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-222">Move each control down a row, by increasing the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> by 1.</span></span> 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. <span data-ttu-id="0f6cb-223">Définir le <xref:System.Windows.Controls.Panel.Background%2A> de le <xref:System.Windows.Controls.Grid> soit le fichier image watermark.png.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-223">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the watermark.png image file.</span></span> 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. <span data-ttu-id="0f6cb-224">Avant du <xref:System.Windows.Controls.Border>, ajoutez un <xref:System.Windows.Controls.Label> avec le contenu « View Expense Report » comme titre de la page.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-224">Before the <xref:System.Windows.Controls.Border>, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report" to be the title of the page.</span></span> 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. <span data-ttu-id="0f6cb-225">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-225">Build and run the application.</span></span> 
  
 <span data-ttu-id="0f6cb-226">L’illustration suivante montre les résultats de cette section.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-226">The following illustration shows the results of this section.</span></span> 
  
 <span data-ttu-id="0f6cb-227">![Exemple de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span><span class="sxs-lookup"><span data-stu-id="0f6cb-227">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span></span>  
  
## <a name="adding-code-to-handle-events"></a><span data-ttu-id="0f6cb-228">Ajout d’un code pour gérer des événements</span><span class="sxs-lookup"><span data-stu-id="0f6cb-228">Adding code to handle events</span></span>  
  
1. <span data-ttu-id="0f6cb-229">Ouvrez ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-229">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="0f6cb-230">Ajouter un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements à la <xref:System.Windows.Controls.Button> élément.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-230">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="0f6cb-231">Pour plus d’informations, consultez [Comment : créer un gestionnaire d’événements Simple](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-231">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span> 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. <span data-ttu-id="0f6cb-232">Ouvrez ExpenseItHome.xaml.vb ou ExpenseItHome.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-232">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="0f6cb-233">Ajoutez le code suivant à la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements, ce qui entraîne la fenêtre pour accéder au fichier ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-233">Add the following code to the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler, which causes the window to navigate to the ExpenseReportPage.xaml file.</span></span> 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a><span data-ttu-id="0f6cb-234">Création de l’interface utilisateur pour ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="0f6cb-234">Creating the UI for ExpenseReportPage</span></span>  
 <span data-ttu-id="0f6cb-235">ExpenseReportPage.xaml affiche la note de frais correspondant à la personne qui a été sélectionnée dans ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-235">ExpenseReportPage.xaml displays the expense report for the person that was selected on the ExpenseItHome.xaml.</span></span> <span data-ttu-id="0f6cb-236">Cette section ajoute des contrôles et crée le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-236">This section adds controls and creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for ExpenseReportPage.xaml.</span></span> <span data-ttu-id="0f6cb-237">Cette section ajoute aussi des couleurs d’arrière-plan et de remplissage vers les différents [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-237">This section also adds background and fill colors to the various [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> 
  
1. <span data-ttu-id="0f6cb-238">Ouvrez ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-238">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="0f6cb-239">Ajoutez le XAML suivant entre les balises <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-239">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
     <span data-ttu-id="0f6cb-240">Cette interface utilisateur est similaire à l’interface utilisateur créée sur ExpenseItHome.xaml, sauf les données du rapport s’affiche dans un <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-240">This UI is similar to the UI created on ExpenseItHome.xaml except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span> 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. <span data-ttu-id="0f6cb-241">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-241">Build and run the application.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="0f6cb-242">Si vous obtenez une erreur qui le <xref:System.Windows.Controls.DataGrid> est introuvable ou n’existe pas, assurez-vous que votre projet cible le .NET Framework 4 ou version ultérieur.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-242">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="0f6cb-243">Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-243">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
4. <span data-ttu-id="0f6cb-244">Cliquez sur le **vue** bouton.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-244">Click the **View** button.</span></span> 
  
     <span data-ttu-id="0f6cb-245">La page de note de frais s’affiche.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-245">The expense report page appears.</span></span> 
  
 <span data-ttu-id="0f6cb-246">L’illustration suivante montre le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments ajoutés à ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-246">The following illustration shows the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements added to ExpenseReportPage.xaml.</span></span> <span data-ttu-id="0f6cb-247">Notez que le bouton de navigation Précédent est activé.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-247">Notice that the back navigation button is enabled.</span></span> 
  
 <span data-ttu-id="0f6cb-248">![Exemple de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span><span class="sxs-lookup"><span data-stu-id="0f6cb-248">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span></span>  
  
## <a name="styling-controls"></a><span data-ttu-id="0f6cb-249">Contrôles de styles</span><span class="sxs-lookup"><span data-stu-id="0f6cb-249">Styling controls</span></span>  
 <span data-ttu-id="0f6cb-250">L’apparence des différents éléments peut souvent être la même pour tous les éléments du même type dans un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f6cb-250">The appearance of various elements can often be the same for all elements of the same type in a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> <span data-ttu-id="0f6cb-251">L’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] utilise des styles pour pouvoir réutiliser l’apparence sur plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-251">[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] uses styles to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="0f6cb-252">La réutilisation des styles permet de simplifier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] création et la gestion.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-252">The reusability of styles helps to simplify [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] creation and management.</span></span> <span data-ttu-id="0f6cb-253">Pour plus d’informations sur les styles, consultez [styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-253">For more information about styles, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span> <span data-ttu-id="0f6cb-254">Cette section remplace par des styles les attributs d’élément qui ont été définis lors des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-254">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span> 
  
1. <span data-ttu-id="0f6cb-255">Ouvrez Application.xaml ou App.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-255">Open Application.xaml or App.xaml.</span></span> 
  
2. <span data-ttu-id="0f6cb-256">Ajoutez le code XAML suivant entre les <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> balises :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-256">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     <span data-ttu-id="0f6cb-257">Cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ajoute les styles suivants :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-257">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adds the following styles:</span></span>  
  
    -  <span data-ttu-id="0f6cb-258">`headerTextStyle`: pour mettre en forme le titre de la page <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-258">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="0f6cb-259">`labelStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Label> .</span><span class="sxs-lookup"><span data-stu-id="0f6cb-259">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span> 
  
    -  <span data-ttu-id="0f6cb-260">`columnHeaderStyle`: pour mettre en forme <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-260">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span> 
  
    -  <span data-ttu-id="0f6cb-261">`listHeaderStyle`: pour mettre en forme les contrôles <xref:System.Windows.Controls.Border> de l’en-tête de liste.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-261">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span> 
  
    -  <span data-ttu-id="0f6cb-262">`listHeaderTextStyle`: Pour mettre en forme l’en-tête de liste <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-262">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="0f6cb-263">`buttonStyle`: Pour mettre en forme le <xref:System.Windows.Controls.Button> sur ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-263">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span> 
  
     <span data-ttu-id="0f6cb-264">Notez que les styles sont des ressources et des enfants de le <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> élément de propriété.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-264">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="0f6cb-265">À cet emplacement, les styles sont appliqués à tous les éléments d’une application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-265">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="0f6cb-266">Pour obtenir un exemple d’utilisation des ressources dans un [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, consultez [utiliser les ressources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-266">For an example of using resources in a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span> 
  
3. <span data-ttu-id="0f6cb-267">Ouvrez ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-267">Open ExpenseItHome.xaml.</span></span> 
  
4. <span data-ttu-id="0f6cb-268">Remplacez tout le contenu entre les <xref:System.Windows.Controls.Grid> éléments avec le code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-268">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     <span data-ttu-id="0f6cb-269">Les propriétés qui définissent l’apparence de chaque contrôle, comme <xref:System.Windows.VerticalAlignment> et <xref:System.Windows.Media.FontFamily> , sont supprimées et remplacées lors de l’application de styles.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-269">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="0f6cb-270">Par exemple, le `headerTextStyle` est appliqué à la « View Expense Report » <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-270">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span> 
  
5. <span data-ttu-id="0f6cb-271">Ouvrez ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-271">Open ExpenseReportPage.xaml.</span></span> 
  
6. <span data-ttu-id="0f6cb-272">Remplacez tout le contenu entre les <xref:System.Windows.Controls.Grid> éléments avec le code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-272">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     <span data-ttu-id="0f6cb-273">Des styles sont ajoutés aux éléments <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.Border> .</span><span class="sxs-lookup"><span data-stu-id="0f6cb-273">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span> 
  
7. <span data-ttu-id="0f6cb-274">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-274">Build and run the application.</span></span> 
  
     <span data-ttu-id="0f6cb-275">Après avoir ajouté le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans cette section, l’application recherche le même comme avant la mise à jour avec les styles.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-275">After adding the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] in this section, the application looks the same as it did before being updated with styles.</span></span> 
  
## <a name="binding-data-to-a-control"></a><span data-ttu-id="0f6cb-276">Liaison de données à un contrôle</span><span class="sxs-lookup"><span data-stu-id="0f6cb-276">Binding data to a control</span></span>  
 <span data-ttu-id="0f6cb-277">Dans cette section, vous créez le [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] données liées à différents contrôles.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-277">In this section, you create the [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data that is bound to various controls.</span></span> 
  
1. <span data-ttu-id="0f6cb-278">Ouvrez ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-278">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="0f6cb-279">Après l’ouverture <xref:System.Windows.Controls.Grid> élément, ajoutez le code XAML suivant pour créer un <xref:System.Windows.Data.XmlDataProvider> qui contient les données pour chaque personne.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-279">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person.</span></span> 
  
     <span data-ttu-id="0f6cb-280">Les données sont créées en tant qu’un <xref:System.Windows.Controls.Grid> ressource.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-280">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="0f6cb-281">Les données sont normalement chargées en tant que fichier, mais pour des raisons pratiques, elles sont ajoutées inline.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-281">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. <span data-ttu-id="0f6cb-282">Dans le <xref:System.Windows.Controls.Grid> ressource, ajoutez le code suivant <xref:System.Windows.DataTemplate>, qui définit comment afficher les données dans le <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-282">In the <xref:System.Windows.Controls.Grid> resource, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="0f6cb-283">Pour plus d’informations sur les modèles de données, consultez [Vue d’ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-283">For more information about data templates, see [Data Templating Overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. <span data-ttu-id="0f6cb-284">Remplacer la <xref:System.Windows.Controls.ListBox> avec le code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-284">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     <span data-ttu-id="0f6cb-285">Ce code XAML lie le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété de la <xref:System.Windows.Controls.ListBox> à la source de données et applique le modèle de données en tant que le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-285">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span> 
  
## <a name="connecting-data-to-controls"></a><span data-ttu-id="0f6cb-286">Connexion de données aux contrôles</span><span class="sxs-lookup"><span data-stu-id="0f6cb-286">Connecting data to controls</span></span>  
 <span data-ttu-id="0f6cb-287">Dans cette section, vous écrivez le code qui Récupère l’élément actuel est sélectionné dans la liste de personnes sur la page ExpenseItHome.xaml et sa référence au constructeur de `ExpenseReportPage` lors de l’instanciation.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-287">In this section, you write the code that retrieves the current item that is selected in the list of people on the ExpenseItHome.xaml page, and passes its reference to the constructor of `ExpenseReportPage` during instantiation.</span></span> <span data-ttu-id="0f6cb-288">`ExpenseReportPage` définit son contexte de données avec l’élément passé, c’est-à-dire l’élément auquel les contrôles définis dans ExpenseReportPage.xaml seront liés.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-288">`ExpenseReportPage` sets its data context with the passed item, which is what the controls defined in ExpenseReportPage.xaml will bind to.</span></span> 
  
1. <span data-ttu-id="0f6cb-289">Ouvrez ExpenseReportPage.xaml.vb ou ExpenseReportPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-289">Open ExpenseReportPage.xaml.vb or ExpenseReportPage.xaml.cs.</span></span> 
  
2. <span data-ttu-id="0f6cb-290">Ajoutez un constructeur qui prend un objet de façon à pouvoir transmettre les données de note de frais de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-290">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. <span data-ttu-id="0f6cb-291">Ouvrez ExpenseItHome.xaml.vb ou ExpenseItHome.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-291">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="0f6cb-292">Modifier la <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements pour appeler le constructeur de nouveau en passant les données de rapport de frais de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-292">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a><span data-ttu-id="0f6cb-293">Conception de styles pour les données avec des modèles de données</span><span class="sxs-lookup"><span data-stu-id="0f6cb-293">Styling data with data templates</span></span>  
 <span data-ttu-id="0f6cb-294">Dans cette section, vous mettez à jour le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour chaque élément de données lié aux listes à l’aide de modèles de données.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-294">In this section, you update the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for each item in the data bound lists by using data templates.</span></span> 
  
1. <span data-ttu-id="0f6cb-295">Ouvrez ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-295">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="0f6cb-296">Lier le contenu de la « Nom » et « Département » <xref:System.Windows.Controls.Label> éléments pour les données appropriées de propriété source.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-296">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="0f6cb-297">Pour plus d’informations sur la liaison de données, consultez [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f6cb-297">For more information about data binding, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. <span data-ttu-id="0f6cb-298">Après l’ouverture <xref:System.Windows.Controls.Grid> élément, ajouter les modèles de données suivants, qui définissent comment afficher les données de rapport de frais.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-298">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data.</span></span>  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. <span data-ttu-id="0f6cb-299">Appliquer les modèles à la <xref:System.Windows.Controls.DataGrid> rapporter des données de colonnes qui affichent la dépense.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-299">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span> 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. <span data-ttu-id="0f6cb-300">Générez et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-300">Build and run the application.</span></span> 
  
6. <span data-ttu-id="0f6cb-301">Sélectionnez une personne, cliquez sur le **vue** bouton.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-301">Select a person and click the **View** button.</span></span> 
  
 <span data-ttu-id="0f6cb-302">L’illustration suivante montre les deux pages de l’application ExpenseIt avec les contrôles, la disposition, les styles, la liaison de données et les modèles de données appliqués.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-302">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied.</span></span> 
  
 <span data-ttu-id="0f6cb-303">![Exemples de capture d’écran ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span><span class="sxs-lookup"><span data-stu-id="0f6cb-303">![ExpenseIt sample screen shots](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="0f6cb-304">meilleures pratiques recommandées.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-304">Best practices</span></span>  
 <span data-ttu-id="0f6cb-305">Cet exemple, dont le but est d’illustrer une fonctionnalité spécifique de WPF, ne respecte pas les bonnes pratiques en matière de développement d’applications.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-305">This sample demonstrates a specific feature of WPF and, consequently, does not follow application development best practices.</span></span> <span data-ttu-id="0f6cb-306">Pour une couverture complète de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application meilleures pratiques de développement, consultez les rubriques suivantes comme il convient :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-306">For comprehensive coverage of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and the [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application development best practices, see the following topics as appropriate:</span></span>  
  
-   <span data-ttu-id="0f6cb-307">Accessibilité - [Meilleures pratiques en matière d’accessibilité](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span><span class="sxs-lookup"><span data-stu-id="0f6cb-307">Accessibility - [Accessibility Best Practices](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span></span>  
  
-   <span data-ttu-id="0f6cb-308">Sécurité - [sécurité](../../../../docs/framework/wpf/security-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="0f6cb-308">Security - [Security](../../../../docs/framework/wpf/security-wpf.md)</span></span>  
  
-   <span data-ttu-id="0f6cb-309">Localisation - [Vue d’ensemble de la globalisation et de la localisation WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="0f6cb-309">Localization - [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span></span>  
  
-   <span data-ttu-id="0f6cb-310">Performances - [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span><span class="sxs-lookup"><span data-stu-id="0f6cb-310">Performance - [Optimizing WPF Application Performance](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span></span>  
  
## <a name="whats-next"></a><span data-ttu-id="0f6cb-311">Quelle est la suite</span><span class="sxs-lookup"><span data-stu-id="0f6cb-311">What's next</span></span>  
 <span data-ttu-id="0f6cb-312">Vous avez maintenant un certain nombre de techniques à votre disposition pour la création d’un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à l’aide de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f6cb-312">You now have a number of techniques at your disposal for creating a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] using [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span> <span data-ttu-id="0f6cb-313">Vous devez maintenant avoir une bonne connaissance des blocs de construction de base de données liées [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-313">You should now have a broad understanding of the basic building blocks of a data-bound [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application.</span></span> <span data-ttu-id="0f6cb-314">Cette rubrique est loin d’être exhaustive, mais j’espère qu’elle vous incitera à découvrir par vous-même d’autres techniques au-delà de celles traitées ici.</span><span class="sxs-lookup"><span data-stu-id="0f6cb-314">This topic is by no means exhaustive, but hopefully you also now have a sense of some of the possibilities you might discover on your own beyond the techniques in this topic.</span></span> 
  
 <span data-ttu-id="0f6cb-315">Pour plus d’informations sur les modèles d’architecture et de programmation WPF, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-315">For more information about the WPF architecture and programming models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0f6cb-316">Architecture de WPF</span><span class="sxs-lookup"><span data-stu-id="0f6cb-316">WPF Architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [<span data-ttu-id="0f6cb-317">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="0f6cb-317">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [<span data-ttu-id="0f6cb-318">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="0f6cb-318">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [<span data-ttu-id="0f6cb-319">Disposition</span><span class="sxs-lookup"><span data-stu-id="0f6cb-319">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
  
 <span data-ttu-id="0f6cb-320">Pour plus d’informations sur la création d’applications, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f6cb-320">For more information about creating applications, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0f6cb-321">Développement de l’application</span><span class="sxs-lookup"><span data-stu-id="0f6cb-321">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [<span data-ttu-id="0f6cb-322">Contrôles</span><span class="sxs-lookup"><span data-stu-id="0f6cb-322">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
  
-   [<span data-ttu-id="0f6cb-323">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="0f6cb-323">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [<span data-ttu-id="0f6cb-324">Graphiques et multimédia</span><span class="sxs-lookup"><span data-stu-id="0f6cb-324">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [<span data-ttu-id="0f6cb-325">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="0f6cb-325">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a><span data-ttu-id="0f6cb-326">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f6cb-326">See also</span></span>  
 [<span data-ttu-id="0f6cb-327">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="0f6cb-327">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="0f6cb-328">Vue d’ensemble des modèles de données</span><span class="sxs-lookup"><span data-stu-id="0f6cb-328">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="0f6cb-329">Génération d’une application WPF</span><span class="sxs-lookup"><span data-stu-id="0f6cb-329">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="0f6cb-330">Styles et modèles</span><span class="sxs-lookup"><span data-stu-id="0f6cb-330">Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
