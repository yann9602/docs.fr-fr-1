---
title: "Modules complémentaires de Firefox pour la prise en charge du déploiement d'applications .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5734d58d0cce15c52da6b7242b28ffc8d574060
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Modules complémentaires de Firefox pour la prise en charge du déploiement d'applications .NET
Le [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] plug-in pour Firefox et l’Assistant .NET Framework pour Firefox permettent [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]libres [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]et les applications ClickOnce pour travailler avec le navigateur Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Plug-in pour Firefox WPF  
 Permet de plug-in pour Firefox WPF [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] et libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichiers cible de la navigation et l’exécution au niveau supérieur ou dans un IFRAME HTML dans le navigateur Firefox. Un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application qui peut être publiée sur un serveur Web et lancée dans les navigateurs pris en charge. Faible [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est un fichier XAML qui peut être accédé à et affiché dans les navigateurs pris en charge, comme un fichier XML.  
  
 Le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in pour Firefox est installé avec le [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Windows 7 inclut le [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], mais n’inclut ne pas le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in pour Firefox. Vous ne pouvez pas installer le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in pour Firefox sur Windows 7.  
  
 Le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] n’inclut pas le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in pour Firefox. Toutefois, si les deux le [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] sont, le plug-in pour Firefox WPF est installé avec le [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Par conséquent [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] applications fonctionne toujours car l’hôte WPF chargera la version correcte de l’infrastructure. Pour plus d’informations, consultez [hôte WPF (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>assistant .NET Framework pour Firefox  
 L’Assistant .NET Framework pour Firefox permet à des applications ClickOnce autonomes à exécuter à partir du navigateur Firefox. L’Assistant .NET Framework pour Firefox fonctionne de manière identique lorsqu’il est installé avant et après le navigateur Firefox. Lorsque vous lancez le navigateur Firefox et [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] est installé, Firefox recherche et installe l’Assistant .NET Framework pour Firefox. Les utilisateurs peuvent configurer l’Assistant .NET Framework pour Firefox pour effectuer les opérations suivantes :  
  
-   Demander avant d’exécuter l’application ClickOnce.  
  
-   Signaler toutes les versions installées de .NET Framework ou simplement la version la plus récente.  
  
 L’Assistant .NET Framework pour Firefox est inclus dans le [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Pour plus d’informations sur la suppression de l’Assistant .NET Framework pour Firefox, consultez [comment supprimer l’Assistant .NET Framework pour Firefox](http://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’une application WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [Vue d’ensemble des applications du navigateur XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [Détecter si le plug-in WPF de Firefox est installé](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
