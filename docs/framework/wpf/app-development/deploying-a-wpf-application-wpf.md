---
title: "D&#233;ploiement d&#39;une application WPF (WPF) | Microsoft Docs"
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
  - "déploiement (WPF), applications"
  - "applications WPF, déploiement"
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# D&#233;ploiement d&#39;une application WPF (WPF)
Une fois les applications [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] générées, elles doivent être déployées.  [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et le [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] incluent plusieurs technologies de déploiement.  La technologie de déploiement utilisée pour déployer une application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dépend du type d'application.  Cette rubrique fournit une vue d'ensemble des différentes technologies de déploiement et explique leur utilisation avec les spécifications de déploiement de chaque type d'application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
   
  
<a name="Deployment_Technologies"></a>   
## Technologies de déploiement  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et le [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] incluent plusieurs technologies de déploiement, notamment :  
  
-   Déploiement XCopy.  
  
-   Déploiement [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)].  
  
-   Déploiement [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].  
  
<a name="XCopy_Deployment"></a>   
### Déploiement XCopy  
 Le déploiement XCopy fait référence à l'utilisation du programme en ligne de commande XCopy afin de copier des fichiers d'un emplacement vers un autre.  Le déploiement XCopy convient dans les cas suivants :  
  
-   L'application est autonome.  Il n'a pas besoin de mettre à jour le client pour fonctionner.  
  
-   Les fichiers d'application doivent être déplacés d'un emplacement à un autre, par exemple, d'un emplacement de génération \(disque local, partage de fichiers [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)], etc.\) vers un emplacement de publication \(site Web, partage de fichiers [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)], etc.\).  
  
-   L'application ne nécessite pas d'interface intégrée \(raccourci du menu Démarrer, icône sur le Bureau, etc.\).  
  
 XCopy convient pour les scénarios de déploiement simples. Toutefois, il est limité lorsque des fonctions de déploiement plus complexes sont requises.  En particulier, l'utilisation de XCopy entraîne souvent une surcharge de temps afin de créer, d'exécuter et de gérer des scripts permettant de gérer le déploiement de manière fiable.  En outre, XCopy ne prend pas en charge le versioning, la désinstallation ou la restauration.  
  
<a name="Windows_Installer"></a>   
### Windows Installer  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] permet d'empaqueter des applications en tant qu'exécutables autonomes qui peuvent être facilement distribués aux clients et exécutés.  Par ailleurs, [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] est installé avec [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et permet l'intégration au Bureau, le menu Démarrer et le Panneau de configuration Programmes.  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] simplifie l'installation et la désinstallation d'applications, mais ne fournit pas de fonctions permettant de garantir que les applications installées sont actualisées du point de vue du versioning.  
  
 Pour plus d'informations sur [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)], consultez [Windows Installer Deployment](http://msdn.microsoft.com/fr-fr/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
<a name="ClickOnce_Deployment"></a>   
### Déploiement ClickOnce  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] permet le déploiement d'applications de style Web pour les applications non Web. Les applications sont publiées vers et déployées à partir du Web ou de serveurs de fichiers.  [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] ne prend pas en charge l'ensemble des fonctionnalités clientes proposées par les applications installées par [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Toutefois, il prend en charge un sous\-ensemble qui intègre les éléments suivants :  
  
-   Intégration au menu Démarrer et au Panneau de configuration Programmes.  
  
-   Versioning, restauration et désinstallation.  
  
-   Mode d'installation en ligne, qui lance toujours une application à partir de l'emplacement de déploiement.  
  
-   Mise à jour automatique lorsque les nouvelles versions sont diffusées.  
  
-   Inscription d'extensions de fichiers.  
  
 Pour plus d'informations sur [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], consultez [Sécurité et déploiement ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md).  
  
<a name="Deploying_WPF_Applications"></a>   
## Déploiement d'applications WPF  
 Les options de déploiement d'une application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dépendent du type d'application.  Dans une perspective de déploiement, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a trois types d'application significatifs :  
  
-   Applications autonomes.  
  
-   Applications [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage.  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### Déploiement d'applications autonomes  
 Les applications autonomes sont déployées à l'aide de [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] ou de [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)].  Dans tous les cas, pour pouvoir être exécutées, les applications autonomes nécessitent un niveau de confiance totale.  La confiance totale est accordée automatiquement aux applications autonomes déployées à l'aide de [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)],  mais pas aux applications autonomes déployées à l'aide de [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)].  En lieu et place, [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] affiche une boîte de dialogue d'avertissement de sécurité que l'utilisateur doit accepter avant de pouvoir installer une application autonome.  Si l'avertissement est accepté, l'application autonome est installée et bénéficie de la confiance totale.  Dans le cas contraire, l'application autonome n'est pas installée.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### Déploiement d'applications XAML à balisage  
 Les pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage sont généralement publiées sur des serveurs Web, comme des pages [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)], et peuvent être affichées à l'aide d'[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  Les pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage sont exécutées dans un bac à sable \(sandbox\) de sécurité à niveau de confiance partiel en fonction de restrictions définies par le jeu d'autorisations de la zone Internet.  Ainsi, les applications Web [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] disposent d'un bac à sable \(sandbox\) de sécurité équivalent.  
  
 Pour plus d'informations sur la sécurité pour les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consultez [Sécurité](../../../../docs/framework/wpf/security-wpf.md).  
  
 Les pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage peuvent être installées sur un système de fichier local à l'aide de XCopy ou de [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)].  Ces pages peuvent être affichées à l'aide d'[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] ou de l'Explorateur [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)].  
  
 Pour plus d'informations concernant XAML, consultez [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### Déploiement d'applications du navigateur XAML  
 Les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sont des applications compilées qui nécessitent le déploiement des trois fichiers suivants :  
  
-   *NomApplication*.exe : fichier d'application de l'assembly exécutable.  
  
-   *NomApplication*.xbap : manifeste de déploiement.  
  
-   *NomApplication*.exe.manifest : manifeste d'application.  
  
> [!NOTE]
>  Pour plus d'informations sur les manifestes de déploiement et d'application, consultez [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Ces fichiers sont produits lorsqu'une application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est générée.  Pour plus d'informations, consultez [Comment : créer un projet d'application de navigateur WPF](http://msdn.microsoft.com/fr-fr/72ef4d90-e163-42a1-8df0-ea7ccfd1901f).  À l'instar des pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à balisage, les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sont généralement publiées sur un serveur Web et affichées à l'aide d'[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  
  
 Les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] peuvent être déployées sur les clients à l'aide de toute technique de déploiement.  Toutefois, [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] est recommandé puisqu'il fournit les fonctions suivantes :  
  
1.  Mises à jour automatiques lorsqu'une nouvelle version est publiée.  
  
2.  Privilèges d'élévation pour le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui fonctionne avec la confiance totale.  
  
 Par défaut, ClickOnce publie des fichiers d'application avec l'extension .deploy.  Cela peut s'avérer problématique, mais peut être désactivé.  Pour plus d'informations, consultez [Problèmes de configuration de serveur et de client lors de déploiements ClickOnce](../Topic/Server%20and%20Client%20Configuration%20Issues%20in%20ClickOnce%20Deployments.md).  
  
 Pour plus d'informations sur le déploiement des [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], consultez [Vue d'ensemble des applications de navigateur XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## Installation du .NET Framework  
 Pour exécuter une application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], le [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] doit être installé sur le client.  [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] détecte automatiquement si les clients sont installés avec le [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] en cas d'affichage dans des applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hébergées par un navigateur.  Si le [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] n'est pas installé, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] invite l'utilisateur à l'installer.  
  
 Pour détecter si le [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] est installé, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] intègre un programme d'amorçage inscrit en tant que gestionnaire [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] de secours pour les fichiers de contenu comportant les extensions suivantes : .xaml, .xps, .xbap et .application.  Si vous naviguez vers ces types de fichiers et si le [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] n'est pas installé sur le client, le programme d'amorçage demande l'autorisation de l'installer.  Si l'utilisateur n'accorde pas son autorisation, [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] et l'application ne sont pas installés.  
  
 Si l'utilisateur accorde son autorisation, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] télécharge et installe [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] à l'aide du service [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)].  Une fois l'installation du [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] terminée, le fichier demandé à l'origine est ouvert dans une nouvelle fenêtre de navigateur.  
  
 La détection automatique du [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] est disponible sur les clients [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)] et [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] ou versions ultérieures, sur lesquels [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] est installé.  
  
 Pour plus d'informations, consultez [Déploiement d'applications et du .NET Framework](../../../../docs/framework/deployment/net-framework-and-applications.md).  
  
## Voir aussi  
 [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [Sécurité](../../../../docs/framework/wpf/security-wpf.md)