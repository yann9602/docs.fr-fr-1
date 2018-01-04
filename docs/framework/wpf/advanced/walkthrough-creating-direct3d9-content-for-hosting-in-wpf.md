---
title: "Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1a5d70807541a0a3faf6bc99a3ced42827efd72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="e7fa1-102">Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF</span><span class="sxs-lookup"><span data-stu-id="e7fa1-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="e7fa1-103">Cette procédure pas à pas montre comment créer un contenu Direct3D9 à héberger dans une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="e7fa1-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="e7fa1-104">Pour plus d’informations sur l’hébergement de contenu Direct3D9 dans les applications WPF, consultez [WPF et Direct3D9 interopérabilité](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="e7fa1-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span></span>  
  
 <span data-ttu-id="e7fa1-105">Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7fa1-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="e7fa1-106">Créez un projet Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-106">Create a Direct3D9 project.</span></span>  
  
-   <span data-ttu-id="e7fa1-107">Configurer le projet Direct3D9 à héberger dans une application WPF.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>  
  
 <span data-ttu-id="e7fa1-108">Lorsque vous avez terminé, vous aurez une DLL qui contient le contenu Direct3D9 pour une utilisation dans une application WPF.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e7fa1-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e7fa1-109">Prerequisites</span></span>  
 <span data-ttu-id="e7fa1-110">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="e7fa1-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="e7fa1-111">.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-111">.</span></span>  
  
-   <span data-ttu-id="e7fa1-112">SDK DirectX 9or plus tard.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-112">DirectX SDK 9or later.</span></span>  
  
## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="e7fa1-113">Création du projet Direct3D9</span><span class="sxs-lookup"><span data-stu-id="e7fa1-113">Creating the Direct3D9 Project</span></span>  
 <span data-ttu-id="e7fa1-114">La première étape consiste à créer et configurer le projet Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-114">The first step is to create and configure the Direct3D9 project.</span></span>  
  
#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="e7fa1-115">Pour créer le projet Direct3D9</span><span class="sxs-lookup"><span data-stu-id="e7fa1-115">To create the Direct3D9 project</span></span>  
  
1.  <span data-ttu-id="e7fa1-116">Créez un projet Win32 en C++ nommé `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>  
  
     <span data-ttu-id="e7fa1-117">L’Assistant Application Win32 s’ouvre et affiche l’écran d’accueil.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>  
  
2.  <span data-ttu-id="e7fa1-118">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-118">Click **Next**.</span></span>  
  
     <span data-ttu-id="e7fa1-119">L’écran des paramètres de l’Application s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-119">The Application Settings screen appears.</span></span>  
  
3.  <span data-ttu-id="e7fa1-120">Dans le **type d’Application :** section, sélectionnez le **DLL** option.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-120">In the **Application type:** section, select the **DLL** option.</span></span>  
  
4.  <span data-ttu-id="e7fa1-121">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-121">Click **Finish**.</span></span>  
  
     <span data-ttu-id="e7fa1-122">Le projet D3DContent est généré.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-122">The D3DContent project is generated.</span></span>  
  
5.  <span data-ttu-id="e7fa1-123">Dans l’Explorateur de solutions, cliquez sur le projet D3DContent, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>  
  
     <span data-ttu-id="e7fa1-124">Le **les Pages de propriétés de D3DContent** boîte de dialogue s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-124">The **D3DContent Property Pages** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="e7fa1-125">Sélectionnez le **C/C++** nœud.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-125">Select the **C/C++** node.</span></span>  
  
7.  <span data-ttu-id="e7fa1-126">Dans le **autres répertoires Include** Indiquez l’emplacement de DirectX inclure le dossier.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="e7fa1-127">L’emplacement par défaut de ce dossier est %ProgramFiles%\Microsoft DirectX SDK (*version*) \Include.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>  
  
8.  <span data-ttu-id="e7fa1-128">Double-cliquez sur le **l’éditeur de liens** nœud pour le développer.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-128">Double-click the **Linker** node to expand it.</span></span>  
  
9. <span data-ttu-id="e7fa1-129">Dans le **répertoires de bibliothèques supplémentaires** champ, spécifiez l’emplacement du dossier de bibliothèques DirectX.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="e7fa1-130">L’emplacement par défaut de ce dossier est %ProgramFiles%\Microsoft DirectX SDK (*version*) \Lib\x86.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>  
  
10. <span data-ttu-id="e7fa1-131">Sélectionnez le **entrée** nœud.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-131">Select the **Input** node.</span></span>  
  
11. <span data-ttu-id="e7fa1-132">Dans le **dépendances supplémentaires** champ, ajoutez le `d3d9.lib` et `d3dx9.lib` fichiers.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>  
  
12. <span data-ttu-id="e7fa1-133">Dans l’Explorateur de solutions, ajoutez un nouveau fichier de définition de module (.def) nommé `D3DContent.def` au projet.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>  
  
## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="e7fa1-134">Création du contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="e7fa1-134">Creating the Direct3D9 Content</span></span>  
 <span data-ttu-id="e7fa1-135">Pour obtenir des performances optimales, votre contenu Direct3D9 doit utiliser des paramètres particuliers.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="e7fa1-136">Le code suivant montre comment créer une surface Direct3D9 qui possède les meilleures caractéristiques de performances.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="e7fa1-137">Pour plus d’informations, consultez [considérations sur les performances de Direct3D9 et interopérabilité WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="e7fa1-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>  
  
#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="e7fa1-138">Pour créer le Direct3D9 contenu</span><span class="sxs-lookup"><span data-stu-id="e7fa1-138">To create the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="e7fa1-139">À l’aide de l’Explorateur de solutions, ajoutez les trois classes C++ au projet portant le nom suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>  
  
     <span data-ttu-id="e7fa1-140">`CRenderer`(avec destructeur virtuel)</span><span class="sxs-lookup"><span data-stu-id="e7fa1-140">`CRenderer` (with virtual destructor)</span></span>  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  <span data-ttu-id="e7fa1-141">Ouvrez Renderer.h dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  <span data-ttu-id="e7fa1-142">Ouvrez Renderer.cpp dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  <span data-ttu-id="e7fa1-143">Ouvrez RendererManager.h dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  <span data-ttu-id="e7fa1-144">Ouvrez RendererManager.cpp dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  <span data-ttu-id="e7fa1-145">Ouvrez TriangleRenderer.h dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  <span data-ttu-id="e7fa1-146">Ouvrez TriangleRenderer.cpp dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  <span data-ttu-id="e7fa1-147">Ouvrez stdafx.h dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. <span data-ttu-id="e7fa1-148">Ouvrez dllmain.cpp dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. <span data-ttu-id="e7fa1-149">Ouvrez D3DContent.def dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-149">Open D3DContent.def in the code editor.</span></span>  
  
11. <span data-ttu-id="e7fa1-150">Remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-150">Replace the automatically generated code with the following code.</span></span>  
  
    ```  
    LIBRARY "D3DContent"  
  
    EXPORTS  
  
    SetSize  
    SetAlpha  
    SetNumDesiredSamples  
    SetAdapter  
  
    GetBackBufferNoRef  
    Render  
    Destroy  
    ```  
  
12. <span data-ttu-id="e7fa1-151">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-151">Build the project.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e7fa1-152">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e7fa1-152">Next Steps</span></span>  
  
-   <span data-ttu-id="e7fa1-153">Héberger le contenu Direct3D9 dans une application WPF.</span><span class="sxs-lookup"><span data-stu-id="e7fa1-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="e7fa1-154">Pour plus d’informations, consultez [procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="e7fa1-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7fa1-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7fa1-155">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="e7fa1-156">Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF</span><span class="sxs-lookup"><span data-stu-id="e7fa1-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [<span data-ttu-id="e7fa1-157">Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF</span><span class="sxs-lookup"><span data-stu-id="e7fa1-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
