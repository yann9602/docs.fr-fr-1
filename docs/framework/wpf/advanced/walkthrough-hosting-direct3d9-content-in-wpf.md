---
title: "Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement de contenu Direct3D9 dans WPF | Microsoft Docs"
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
  - "Direct3D9 (interopérabilité WPF), héberger du contenu Direct3D9"
  - "WPF, héberger du contenu Direct3D9"
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Proc&#233;dure pas &#224; pas&#160;: h&#233;bergement de contenu Direct3D9 dans WPF
Cette procédure pas à pas indique comment héberger du contenu Direct3D9 dans une application Windows Presentation Foundation \(WPF\).  
  
 Dans cette procédure pas à pas, vous allez effectuer les tâches suivantes :  
  
-   Créer un projet WPF pour héberger du contenu Direct3D9.  
  
-   Importer le contenu Direct3D9.  
  
-   Afficher le contenu Direct3D9 à l'aide de la classe <xref:System.Windows.Interop.D3DImage>.  
  
 Lorsque vous aurez terminé, vous saurez comment héberger du contenu Direct3D9 dans une application WPF.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Kit de développement DirectX \(SDK\) 9 ou version ultérieure.  
  
-   Une DLL qui contient le contenu Direct3D9 dans un format compatible avec WPF.  Pour plus d'informations, consultez [Interopérabilité WPF et Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) et [Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## Création du projet WPF  
 La première étape consiste à créer le projet pour l'application WPF.  
  
#### Pour créer le projet WPF  
  
-   Créez un projet d'application WPF dans Visual C\# et nommez\-le `D3DHost`.  Pour plus d'informations, consultez [Comment : créer un projet d'application WPF](http://msdn.microsoft.com/fr-fr/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
     MainWindow.xaml s'ouvre dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## Importation du contenu Direct3D9  
 Vous pouvez importer le contenu Direct3D9 à partir d'une DLL non managée à l'aide de l'attribut `DllImport`.  
  
#### Pour importer le contenu Direct3D9  
  
1.  Ouvrez MainWindow.xaml.cs dans l'éditeur de code.  
  
2.  Remplacez le code généré automatiquement par le code suivant.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## Hébergement du contenu Direct3D9  
 Pour terminer, utilisez la classe <xref:System.Windows.Interop.D3DImage> pour héberger le contenu Direct3D9.  
  
#### Pour héberger le contenu Direct3D9  
  
1.  Dans MainWindow.xaml, remplacez le code XAML généré automatiquement par le code XAML suivant.  
  
     [!code-xml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  Générez le projet.  
  
3.  Copiez la DLL qui contient le contenu Direct3D9 dans le dossier bin\/Debug.  
  
4.  Appuyez sur F5 pour exécuter le projet.  
  
     Le contenu Direct3D9 s'affiche dans l'application WPF.  
  
## Voir aussi  
 <xref:System.Windows.Interop.D3DImage>   
 [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)