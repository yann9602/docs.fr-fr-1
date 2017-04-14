---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de contenu Direct3D9 &#224; h&#233;berger dans WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Direct3D9 (interopérabilité WPF), créer du contenu Direct3D9"
  - "WPF, créer du contenu Direct3D9"
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation de contenu Direct3D9 &#224; h&#233;berger dans WPF
Cette procédure pas à pas indique comment créer du contenu Direct3D9 à héberger dans une application Windows Presentation Foundation \(WPF\).  Pour plus d'informations sur l'hébergement de contenu Direct3D9 dans les applications WPF, consultez [Interopérabilité WPF et Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
 Dans cette procédure pas à pas, vous allez effectuer les tâches suivantes :  
  
-   Créer un projet Direct3D9.  
  
-   Configurer le projet Direct3D9 à héberger dans une application WPF.  
  
 Lorsque vous aurez terminé, vous obtiendrez une DLL qui comporte le contenu Direct3D9 à utiliser dans une application WPF.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Kit de développement DirectX \(SDK\) 9 ou version ultérieure.  
  
## Création du projet Direct3D9  
 La première étape consiste à créer et à configurer le projet Direct3D9.  
  
#### Pour créer le projet Direct3D9  
  
1.  Créez un projet Win32 dans C\+\+ et nommez\-le `D3DContent`.  
  
     L'Assistant Application Win32 s'ouvre et affiche son écran de bienvenue.  
  
2.  Cliquez sur **Suivant**.  
  
     L'écran Paramètres de l'application s'affiche.  
  
3.  Dans la section **Type d'application :**, sélectionnez l'option **DLL**.  
  
4.  Cliquez sur **Terminer**.  
  
     Le projet D3DContent est généré.  
  
5.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet D3DContent, puis sélectionnez **Propriétés**.  
  
     La boîte de dialogue **Pages de propriétés de D3DContent** s'affiche.  
  
6.  Sélectionnez le nœud **C\/C\+\+**.  
  
7.  Dans le champ **Autres répertoires Include**, spécifiez l'emplacement du dossier Include DirectX.  L'emplacement par défaut de ce dossier est le suivant : %ProgramFiles%\\Microsoft DirectX SDK \(*version*\)\\Include.  
  
8.  Double\-cliquez sur le nœud **Éditeur de liens** pour le développer.  
  
9. Dans le champ **Répertoires de bibliothèques supplémentaires**, spécifiez l'emplacement du dossier de bibliothèques DirectX.  L'emplacement par défaut de ce dossier est le suivant : %ProgramFiles%\\Microsoft DirectX SDK \(*version*\)\\Lib\\x86.  
  
10. Sélectionnez le nœud **Entrée**.  
  
11. Dans le champ **Dépendances supplémentaires**, ajoutez les fichiers `d3d9.lib` et `d3dx9.lib`.  
  
12. Dans l'Explorateur de solutions, ajoutez un nouveau fichier de définition de module \(.def\) au projet et nommez\-le `D3DContent.def`.  
  
## Création du contenu Direct3D9  
 Pour optimiser les performances, votre contenu Direct3D9 doit utiliser des paramètres particuliers.  Le code suivant indique comment créer une surface Direct3D9 qui possède les meilleures caractéristiques de performances.  Pour plus d'informations, consultez [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
#### Pour créer le contenu Direct3D9  
  
1.  À l'aide de l'Explorateur de solutions, ajoutez au projet trois classes C\+\+ portant le nom suivant.  
  
     `CRenderer` \(avec destructeur virtuel\)  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  Ouvrez Renderer.h dans l'éditeur de code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  Ouvrez Renderer.cpp dans l'éditeur de code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  Ouvrez RendererManager.h dans l'éditeur de code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  Ouvrez RendererManager.cpp dans l'éditeur de code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  Ouvrez TriangleRenderer.h dans l'éditeur de code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  Ouvrez TriangleRenderer.cpp dans l'éditeur de code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  Ouvrez stdafx.h dans l'éditeur de code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. Ouvrez dllmain.cpp dans l'éditeur de code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. Ouvrez D3DContent.def dans l'éditeur de code.  
  
11. Remplacez le code généré automatiquement par le code suivant.  
  
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
  
12. Générez le projet.  
  
## Étapes suivantes  
  
-   Hébergez le contenu Direct3D9 dans une application WPF.  Pour plus d'informations, consultez [Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).  
  
## Voir aussi  
 <xref:System.Windows.Interop.D3DImage>   
 [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)   
 [Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)