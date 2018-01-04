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
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF
Cette procédure pas à pas montre comment créer un contenu Direct3D9 à héberger dans une application Windows Presentation Foundation (WPF). Pour plus d’informations sur l’hébergement de contenu Direct3D9 dans les applications WPF, consultez [WPF et Direct3D9 interopérabilité](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   Créez un projet Direct3D9.  
  
-   Configurer le projet Direct3D9 à héberger dans une application WPF.  
  
 Lorsque vous avez terminé, vous aurez une DLL qui contient le contenu Direct3D9 pour une utilisation dans une application WPF.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   SDK DirectX 9or plus tard.  
  
## <a name="creating-the-direct3d9-project"></a>Création du projet Direct3D9  
 La première étape consiste à créer et configurer le projet Direct3D9.  
  
#### <a name="to-create-the-direct3d9-project"></a>Pour créer le projet Direct3D9  
  
1.  Créez un projet Win32 en C++ nommé `D3DContent`.  
  
     L’Assistant Application Win32 s’ouvre et affiche l’écran d’accueil.  
  
2.  Cliquez sur **Suivant**.  
  
     L’écran des paramètres de l’Application s’affiche.  
  
3.  Dans le **type d’Application :** section, sélectionnez le **DLL** option.  
  
4.  Cliquez sur **Terminer**.  
  
     Le projet D3DContent est généré.  
  
5.  Dans l’Explorateur de solutions, cliquez sur le projet D3DContent, puis sélectionnez **propriétés**.  
  
     Le **les Pages de propriétés de D3DContent** boîte de dialogue s’ouvre.  
  
6.  Sélectionnez le **C/C++** nœud.  
  
7.  Dans le **autres répertoires Include** Indiquez l’emplacement de DirectX inclure le dossier. L’emplacement par défaut de ce dossier est %ProgramFiles%\Microsoft DirectX SDK (*version*) \Include.  
  
8.  Double-cliquez sur le **l’éditeur de liens** nœud pour le développer.  
  
9. Dans le **répertoires de bibliothèques supplémentaires** champ, spécifiez l’emplacement du dossier de bibliothèques DirectX. L’emplacement par défaut de ce dossier est %ProgramFiles%\Microsoft DirectX SDK (*version*) \Lib\x86.  
  
10. Sélectionnez le **entrée** nœud.  
  
11. Dans le **dépendances supplémentaires** champ, ajoutez le `d3d9.lib` et `d3dx9.lib` fichiers.  
  
12. Dans l’Explorateur de solutions, ajoutez un nouveau fichier de définition de module (.def) nommé `D3DContent.def` au projet.  
  
## <a name="creating-the-direct3d9-content"></a>Création du contenu Direct3D9  
 Pour obtenir des performances optimales, votre contenu Direct3D9 doit utiliser des paramètres particuliers. Le code suivant montre comment créer une surface Direct3D9 qui possède les meilleures caractéristiques de performances. Pour plus d’informations, consultez [considérations sur les performances de Direct3D9 et interopérabilité WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
#### <a name="to-create-the-direct3d9-content"></a>Pour créer le Direct3D9 contenu  
  
1.  À l’aide de l’Explorateur de solutions, ajoutez les trois classes C++ au projet portant le nom suivant.  
  
     `CRenderer`(avec destructeur virtuel)  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  Ouvrez Renderer.h dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  Ouvrez Renderer.cpp dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  Ouvrez RendererManager.h dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  Ouvrez RendererManager.cpp dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  Ouvrez TriangleRenderer.h dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  Ouvrez TriangleRenderer.cpp dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  Ouvrez stdafx.h dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. Ouvrez dllmain.cpp dans l’éditeur de Code et remplacez le code généré automatiquement par le code suivant.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. Ouvrez D3DContent.def dans l’éditeur de code.  
  
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
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Héberger le contenu Direct3D9 dans une application WPF. Pour plus d’informations, consultez [procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Interop.D3DImage>  
 [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
