---
title: "Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec80eed37777fc7b17b435e1bef63ecbb94bdf46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="f200d-102">Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF</span><span class="sxs-lookup"><span data-stu-id="f200d-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="f200d-103">Cette procédure pas à pas montre comment héberger du contenu Direct3D9 dans une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f200d-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="f200d-104">Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="f200d-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f200d-105">Créez un projet WPF pour héberger le contenu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="f200d-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="f200d-106">Importer le contenu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="f200d-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="f200d-107">Afficher le contenu Direct3D9 à l’aide de la <xref:System.Windows.Interop.D3DImage> classe.</span><span class="sxs-lookup"><span data-stu-id="f200d-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="f200d-108">Lorsque vous avez terminé, vous saurez comment héberger du contenu Direct3D9 dans une application WPF.</span><span class="sxs-lookup"><span data-stu-id="f200d-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f200d-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f200d-109">Prerequisites</span></span>  
 <span data-ttu-id="f200d-110">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="f200d-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="f200d-111">.</span><span class="sxs-lookup"><span data-stu-id="f200d-111">.</span></span>  
  
-   <span data-ttu-id="f200d-112">DirectX (SDK) 9 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f200d-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="f200d-113">Une DLL qui contient le contenu Direct3D9 dans un format compatible avec WPF.</span><span class="sxs-lookup"><span data-stu-id="f200d-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="f200d-114">Pour plus d’informations, consultez [WPF et Direct3D9 interopérabilité](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) et [procédure pas à pas : création de contenu Direct3D9 pour l’hébergement dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="f200d-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="f200d-115">Création du projet WPF</span><span class="sxs-lookup"><span data-stu-id="f200d-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="f200d-116">La première étape consiste à créer le projet d’application WPF.</span><span class="sxs-lookup"><span data-stu-id="f200d-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="f200d-117">Pour créer le projet WPF</span><span class="sxs-lookup"><span data-stu-id="f200d-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="f200d-118">Créer un nouveau projet d’Application WPF dans Visual c# nommé `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="f200d-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="f200d-119">Pour plus d'informations, consultez [Guide pratique pour créer un projet d'application WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="f200d-119">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
     <span data-ttu-id="f200d-120">MainWindow.xaml s’ouvre dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f200d-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="f200d-121">L’importation du contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f200d-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="f200d-122">Vous importez le contenu Direct3D9 à partir d’une DLL non managée à l’aide de la `DllImport` attribut.</span><span class="sxs-lookup"><span data-stu-id="f200d-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="f200d-123">Pour importer le contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f200d-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="f200d-124">Ouvrez MainWindow.xaml.cs dans l’éditeur de Code.</span><span class="sxs-lookup"><span data-stu-id="f200d-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="f200d-125">Remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f200d-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="f200d-126">Hébergement du contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f200d-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="f200d-127">Enfin, utilisez la <xref:System.Windows.Interop.D3DImage> classe pour héberger le contenu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="f200d-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="f200d-128">Pour héberger le contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f200d-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="f200d-129">Dans MainWindow.xaml, remplacez le code XAML généré automatiquement par le code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="f200d-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="f200d-130">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="f200d-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="f200d-131">Copiez la DLL qui contient le contenu Direct3D9 dans le dossier bin/Debug.</span><span class="sxs-lookup"><span data-stu-id="f200d-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="f200d-132">Appuyez sur F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="f200d-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="f200d-133">Le contenu Direct3D9 s’affiche dans l’application WPF.</span><span class="sxs-lookup"><span data-stu-id="f200d-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f200d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f200d-134">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="f200d-135">Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF</span><span class="sxs-lookup"><span data-stu-id="f200d-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
