---
title: "Débuter avec l'encre"
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
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc8ffe9ad68060d9dfbcafe99133a736237a2bb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started-with-ink"></a><span data-ttu-id="4deda-102">Débuter avec l'encre</span><span class="sxs-lookup"><span data-stu-id="4deda-102">Getting Started with Ink</span></span>
<span data-ttu-id="4deda-103">Incorporation d’encre numérique dans vos applications est plus facile que jamais.</span><span class="sxs-lookup"><span data-stu-id="4deda-103">Incorporating digital ink into your applications is easier than ever.</span></span> <span data-ttu-id="4deda-104">Encre a évolué d’être un corollaire à la méthode COM et Windows Forms de la programmation à la réalisation d’une intégration complète dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4deda-104">Ink has evolved from being a corollary to the COM and Windows Forms method of programming to achieving full integration into the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="4deda-105">Vous n’avez pas besoin installer les kits de développement logiciel distincts ou des bibliothèques runtime.</span><span class="sxs-lookup"><span data-stu-id="4deda-105">You do not need to install separate SDKs or runtime libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4deda-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4deda-106">Prerequisites</span></span>  
 <span data-ttu-id="4deda-107">Pour utiliser les exemples suivants, vous devez d’abord installer Microsoft Visual Studio 2005 et le [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4deda-107">To use the following examples, you must first install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="4deda-108">Vous devez également comprendre comment écrire des applications pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4deda-108">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="4deda-109">Pour plus d’informations sur la prise en main de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [procédure pas à pas : Ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="4deda-109">For more information about getting started with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="quick-start"></a><span data-ttu-id="4deda-110">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="4deda-110">Quick Start</span></span>  
 <span data-ttu-id="4deda-111">Cette section vous permet d’écrire un simple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application qui collecte de l’encre.</span><span class="sxs-lookup"><span data-stu-id="4deda-111">This section helps you write a simple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that collects ink.</span></span>  
  
 <span data-ttu-id="4deda-112">Si vous n’avez pas déjà fait, installez Microsoft Visual Studio 2005 et le [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4deda-112">If you haven't already done so, install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="4deda-113">applications généralement doivent être compilées avant de pouvoir afficher, même si elles sont entièrement composent de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4deda-113"> applications usually must be compiled before you can view them, even if they consist entirely of [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="4deda-114">Toutefois, le [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] inclut une application, XamlPad, conçue pour accélérer le processus d’implémentation d’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-en fonction de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4deda-114">However, the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] includes an application, XamlPad, designed to speed up the process of implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-based UI.</span></span> <span data-ttu-id="4deda-115">Vous pouvez utiliser cette application pour afficher et vous entraîner avec les premiers exemples dans ce document.</span><span class="sxs-lookup"><span data-stu-id="4deda-115">You can use that application to view and tinker with the first few samples in this document.</span></span> <span data-ttu-id="4deda-116">Le processus de création d’applications compilées [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est couvert plus loin dans ce document.</span><span class="sxs-lookup"><span data-stu-id="4deda-116">The process of creating compiled applications from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is covered later in this document.</span></span>  
  
 <span data-ttu-id="4deda-117">Pour lancer XAMLPad, cliquez sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Winndows SDK Microsoft**, pointez sur **outils**, puis cliquez sur **XAMLPad**.</span><span class="sxs-lookup"><span data-stu-id="4deda-117">To launch XAMLPad, click the **Start** menu, point to **All Programs**, point to **Microsoft Winndows SDK**, point to **Tools**, and click **XAMLPad**.</span></span> <span data-ttu-id="4deda-118">Dans le volet de rendu, XAMLPad restitue le code XAML dans le volet du code.</span><span class="sxs-lookup"><span data-stu-id="4deda-118">In the rendering pane, XAMLPad renders the XAML code written in the code pane.</span></span> <span data-ttu-id="4deda-119">Vous pouvez modifier le code XAML, et les modifications apparaissent immédiatement dans le volet de rendu.</span><span class="sxs-lookup"><span data-stu-id="4deda-119">You can edit the XAML code, and the changes immediately appear in the rendering pane.</span></span>  
  
#### <a name="got-ink"></a><span data-ttu-id="4deda-120">Vous avez encre ?</span><span class="sxs-lookup"><span data-stu-id="4deda-120">Got Ink?</span></span>  
 <span data-ttu-id="4deda-121">Pour démarrer votre première [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application qui prend en charge les services d’encre :</span><span class="sxs-lookup"><span data-stu-id="4deda-121">To start your first [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that supports ink:</span></span>  
  
1.  <span data-ttu-id="4deda-122">Ouvrez Microsoft Visual Studio 2005</span><span class="sxs-lookup"><span data-stu-id="4deda-122">Open Microsoft Visual Studio 2005</span></span>  
  
2.  <span data-ttu-id="4deda-123">Créer un nouveau **Application WPF (Windows)**</span><span class="sxs-lookup"><span data-stu-id="4deda-123">Create a new **Windows Application (WPF)**</span></span>  
  
3.  <span data-ttu-id="4deda-124">Type `<InkCanvas/>` entre les `<Grid>` balises</span><span class="sxs-lookup"><span data-stu-id="4deda-124">Type `<InkCanvas/>` between the `<Grid>` tags</span></span>  
  
4.  <span data-ttu-id="4deda-125">Appuyez sur **F5** pour lancer votre application dans le débogueur</span><span class="sxs-lookup"><span data-stu-id="4deda-125">Press **F5** to launch your application in the debugger</span></span>  
  
5.  <span data-ttu-id="4deda-126">À l’aide d’un stylet ou une souris, écrire **Bonjour** dans la fenêtre</span><span class="sxs-lookup"><span data-stu-id="4deda-126">Using a stylus or mouse, write **hello world** in the window</span></span>  
  
 <span data-ttu-id="4deda-127">Vous avez écrit l’équivalent d’encre d’une application « hello world » avec des séquences de touches que 12 !</span><span class="sxs-lookup"><span data-stu-id="4deda-127">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>  
  
#### <a name="spice-up-your-application"></a><span data-ttu-id="4deda-128">Enrichir votre Application</span><span class="sxs-lookup"><span data-stu-id="4deda-128">Spice Up Your Application</span></span>  
 <span data-ttu-id="4deda-129">Tirez parti de certaines fonctionnalités de le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4deda-129">Let’s take advantage of some features of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  <span data-ttu-id="4deda-130">Remplacez tout le contenu entre l’ouverture \<fenêtre > et la fermeture de \</Window > balises par le balisage suivant pour obtenir un arrière-plan de pinceau de dégradé sur votre surface d’encre.</span><span class="sxs-lookup"><span data-stu-id="4deda-130">Replace everything between the opening \<Window> and closing \</Window> tags with the following markup to get a gradient brush background on your inking surface.</span></span>  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a><span data-ttu-id="4deda-131">À l’aide d’Animation</span><span class="sxs-lookup"><span data-stu-id="4deda-131">Using Animation</span></span>  
 <span data-ttu-id="4deda-132">Pour vous amuser, animez les couleurs de pinceau de dégradé.</span><span class="sxs-lookup"><span data-stu-id="4deda-132">For fun, let's animate the colors of the gradient brush.</span></span> <span data-ttu-id="4deda-133">Ajoutez le code suivant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] après la fermeture `</InkCanvas>` balise mais avant la fermeture `</Page>` balise.</span><span class="sxs-lookup"><span data-stu-id="4deda-133">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] after the closing `</InkCanvas>` tag but before the closing `</Page>` tag.</span></span>  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a><span data-ttu-id="4deda-134">Ajout de Code après le code XAML</span><span class="sxs-lookup"><span data-stu-id="4deda-134">Adding Some Code Behind the XAML</span></span>  
 <span data-ttu-id="4deda-135">Bien que le XAML facilite la conception de l’interface utilisateur, n’importe quelle application réelle doit ajouter du code pour gérer les événements.</span><span class="sxs-lookup"><span data-stu-id="4deda-135">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="4deda-136">Voici un exemple simple qui effectue un zoom sur l’encre en réponse à un clic droit de la souris :</span><span class="sxs-lookup"><span data-stu-id="4deda-136">Here is a simple example that zooms in on the ink in response to a right-click from a mouse:</span></span>  
  
 <span data-ttu-id="4deda-137">Définir le `MouseRightButtonUp` gestionnaire dans votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="4deda-137">Set the `MouseRightButtonUp` handler in your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span></span>  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 <span data-ttu-id="4deda-138">Dans l’Explorateur de solutions de Visual Studio, développez Windows1.xaml et ouvrez le fichier code-behind, Window1.xaml.cs ou Window1.xaml.vb si vous utilisez Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4deda-138">In Visual Studio’s Solution Explorer, expand Windows1.xaml and open the code-behind file, Window1.xaml.cs or Window1.xaml.vb if you are using Visual Basic.</span></span> <span data-ttu-id="4deda-139">Ajoutez le code de gestionnaire d’événements suivantes :</span><span class="sxs-lookup"><span data-stu-id="4deda-139">Add the following event handler code:</span></span>  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 <span data-ttu-id="4deda-140">Maintenant, exécutez votre application.</span><span class="sxs-lookup"><span data-stu-id="4deda-140">Now, run your application.</span></span> <span data-ttu-id="4deda-141">Ajoutez de l’encre et le bouton droit de la souris ou effectuer un équivalent appuyer et maintenir avec un stylet.</span><span class="sxs-lookup"><span data-stu-id="4deda-141">Add some ink and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>  
  
#### <a name="using-procedural-code-instead-of-xaml"></a><span data-ttu-id="4deda-142">À l’aide des procédures de Code au lieu de XAML</span><span class="sxs-lookup"><span data-stu-id="4deda-142">Using Procedural Code Instead of XAML</span></span>  
 <span data-ttu-id="4deda-143">Vous pouvez accéder à tous les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalités à partir de procédures de code.</span><span class="sxs-lookup"><span data-stu-id="4deda-143">You can access all [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] features from procedural code.</span></span> <span data-ttu-id="4deda-144">Voici une application « Hello Ink World » pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui n’utilise aucun [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] du tout.</span><span class="sxs-lookup"><span data-stu-id="4deda-144">Here is a "Hello Ink World" application for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] that doesn’t use any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] at all.</span></span> <span data-ttu-id="4deda-145">Collez le code ci-dessous dans une Application Console vide dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4deda-145">Paste the code below into an empty Console Application in Visual Studio.</span></span> <span data-ttu-id="4deda-146">Ajouter des références aux assemblys WindowsBase, PresentationCore et PresentationFramework et générez l’application en appuyant sur **F5**:</span><span class="sxs-lookup"><span data-stu-id="4deda-146">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies, and build the application by pressing **F5**:</span></span>  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4deda-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4deda-147">See Also</span></span>  
 [<span data-ttu-id="4deda-148">Encre numérique</span><span class="sxs-lookup"><span data-stu-id="4deda-148">Digital Ink</span></span>](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [<span data-ttu-id="4deda-149">Collecte d'encre</span><span class="sxs-lookup"><span data-stu-id="4deda-149">Collecting Ink</span></span>](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [<span data-ttu-id="4deda-150">Reconnaissance d'écriture manuscrite</span><span class="sxs-lookup"><span data-stu-id="4deda-150">Handwriting Recognition</span></span>](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [<span data-ttu-id="4deda-151">Stockage de l’encre</span><span class="sxs-lookup"><span data-stu-id="4deda-151">Storing Ink</span></span>](../../../../docs/framework/wpf/advanced/storing-ink.md)
