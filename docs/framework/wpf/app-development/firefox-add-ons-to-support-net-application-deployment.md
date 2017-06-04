---
title: "Modules compl&#233;mentaires de Firefox pour la prise en charge du d&#233;ploiement d&#39;applications .NET | Microsoft Docs"
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
  - "déploiement d'applications .NET, déployer dans des composants additionnels Firefox"
  - "assistant .NET Framework pour Firefox"
  - "composants additionnels Firefox pour le déploiement d'applications .NET"
  - "plug-in WPF de Firefox"
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# Modules compl&#233;mentaires de Firefox pour la prise en charge du d&#233;ploiement d&#39;applications .NET
Le plug\-in [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] pour Firefox et l'Assistant .NET Framework pour Firefox permettent d'utiliser les [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libres et les applications ClickOnce dans le navigateur Mozilla Firefox.  
  
## Plug\-in WPF pour Firefox  
 Le plug\-in WPF pour Firefox permet l'accès aux [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] et aux fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libres, ainsi que leur exécution à un niveau supérieur ou au sein d'un IFrame HTML dans le navigateur Firefox.  Un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est une application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pouvant être publiée sur un serveur Web et lancée dans les navigateurs pris en charge.  Un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre est un fichier XAML accessible et affichable depuis les navigateurs pris en charge, tout comme un fichier XML.  
  
 Le plug\-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour Firefox est installé dans le cadre de l'installation de [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)].  Windows 7 inclut [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], mais pas le plug\-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour Firefox. Il n'est pas possible d'installer le plug\-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour Firefox dans Windows 7.  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] n'inclut pas le plug\-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour Firefox. Toutefois, si [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] sont tous deux installés, le plug\-in WPF pour Firefox est installé dans le cadre de l'installation de [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)].  Par conséquent, les applications [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] pourront toujours être exécutées car l'hôte WPF chargera la version appropriée de .NET Framework.  Pour plus d'informations, consultez [Hôte WPF \(PresentationHost.exe\)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md).  
  
## Assistant .NET Framework pour Firefox  
 L'Assistant .NET Framework pour Firefox permet aux applications autonomes ClickOnce d'être exécutées depuis un navigateur Firefox.  Il fonctionne de la même manière, qu'il ait été installé avant ou après le navigateur Firefox.  Lorsque le navigateur Firefox est lancé et que [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] est installé, Firefox recherche et installe l'Assistant .NET Framework pour Firefox.  Les utilisateurs peuvent configurer l'Assistant .NET Framework pour Firefox pour effectuer les opérations suivantes :  
  
-   Afficher une invite avant d'exécuter l'application ClickOnce.  
  
-   Signaler toutes les versions de .NET Framework installées ou uniquement la version la plus récente.  
  
 L'Assistant .NET Framework pour Firefox est compris dans [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)].  Pour plus d'informations sur la désinstallation de l'Assistant .NET Framework pour Firefox, consultez [Comment supprimer l'Assistant .NET Framework pour Firefox](http://go.microsoft.com/fwlink/?LinkId=177944).  
  
## Voir aussi  
 [Déploiement d'une application WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)   
 [Vue d'ensemble des applications de navigateur XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)   
 [Détecter si le plug\-in WPF de Firefox est installé](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)