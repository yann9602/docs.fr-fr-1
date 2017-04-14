---
title: "D&#233;veloppement de l&#39;application | Microsoft Docs"
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
  - "développement d'applications (WPF), à propos de"
  - "WPF, à propos du développement d'applications"
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# D&#233;veloppement de l&#39;application
<a name="introduction"></a> [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] est une infrastructure de présentation qui peut être utilisée pour développer les types d'applications suivants :  
  
-   Applications autonomes \(applications [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] de style traditionnel générées sous forme d'assemblys exécutables qui sont installés et exécutés sur l'ordinateur client\).  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] \(applications composées de pages de navigation générés sous forme d'assemblys exécutables et hébergés par des navigateurs Web tels que [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] ou Mozilla Firefox\).  
  
-   Bibliothèques de contrôles personnalisés \(assemblys non exécutables contenant des contrôles réutilisables\).  
  
-   Bibliothèques de classes \(assemblys non exécutables contenant des classes réutilisables\).  
  
> [!NOTE]
>  L'utilisation de types WPF dans un service Windows est fortement déconseillée.  Si vous tentez d'utiliser ces fonctionnalités dans un service Windows, elles risquent de ne pas fonctionner comme prévu.  
  
 Pour générer cet ensemble d'applications, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implémente une pléthore de services.  Cette rubrique fournit une vue d'ensemble de ces services et explique où trouver plus d'informations.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Application_Management"></a>   
## Gestion d'applications  
 Les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exécutables requièrent généralement un ensemble principal de fonctionnalités qui inclut les opérations suivantes :  
  
-   La création et la gestion de l'infrastructure d'application commune \(y compris la création d'une méthode de point d'entrée et une boucle de messages Windows pour recevoir les messages système et d'entrée\).  
  
-   Le suivi et l'interaction avec la durée de vie d'une application.  
  
-   Récupération et traitement des paramètres de ligne de commande  
  
-   Le partage des propriétés de portée d'application et des ressources [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   La détection et le traitement des exceptions non gérées.  
  
-   Retour de codes de sortie  
  
-   La gestion des fenêtres dans des applications autonomes.  
  
-   Le suivi de la navigation dans [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] et des applications autonomes avec des fenêtres et des cadres de navigation.  
  
 Ces fonctionnalités sont implémentées par la classe <xref:System.Windows.Application> que vous ajoutez à vos applications à l'aide d'une *définition d'application*.  
  
 Pour plus d'informations, consultez [Vue d'ensemble de la gestion d'applications](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## Fichiers de ressources, de contenu et de données d'une application WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] renforce le support principal dans [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] pour les ressources incorporées avec prise en charge de trois types de fichiers de données non exécutables, à savoir les fichiers de ressources, de contenu et de données. Pour plus d'informations,consultez [Fichiers de ressources, de contenu et de données d'une application WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Un composant clé de la prise en charge des fichiers de données WPF non exécutables est la capacité à les identifier et à les charger à l'aide d'un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] unique. Pour plus d'informations, consultez [URI à en\-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## Fenêtres et boîtes de dialogue  
 Les utilisateurs interagissent avec les applications autonomes [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] par le biais de fenêtres.  Le rôle d'une fenêtre est d'héberger le contenu d'une application et de présenter les fonctionnalités de l'application qui permettent généralement aux utilisateurs d'interagir avec le contenu.  Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], les fenêtres sont encapsulées par la classe  <xref:System.Windows.Window> qui prend en charge :  
  
-   La création et l'affichage des fenêtres.  
  
-   L'établissement des relations entre fenêtres parent et fenêtres enfant.  
  
-   La configuration de l'aspect des fenêtres \(par exemple, taille, emplacement, icônes, texte de barre de titre, bordure\).  
  
-   Le suivi et l'interaction avec la durée de vie d'une fenêtre.  
  
 Pour plus d'informations, consultez [Vue d'ensemble des fenêtres WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> prend en charge la capacité de créer un type spécial de fenêtre appelé « boîte de dialogue ».  Les deux types de boîtes de dialogue, modales et non modales, peuvent être créés.  
  
 Pour des raisons de commodité, pour favoriser la réutilisation des éléments et pour garantir aux utilisateurs une expérience cohérente entre les applications, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] présente trois boîtes de dialogue [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] parmi les plus communes, à savoir <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog> et <xref:System.Windows.Controls.PrintDialog>.  
  
 Une boîte de message est un type spécial de boîte de dialogue qui permet d'afficher des informations textuelles importantes aux utilisateurs et de poser des questions simples du type Oui\/Non\/OK\/Annuler.  Vous utilisez la classe <xref:System.Windows.MessageBox> pour créer et afficher des boîtes de messages.  
  
 Pour plus d'informations, consultez [Vue d'ensemble des boîtes de dialogue](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## Navigation  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend en charge la navigation de type Web à l'aide de pages \(<xref:System.Windows.Controls.Page>\) et de liens hypertexte \(<xref:System.Windows.Documents.Hyperlink>\).  La navigation peut être implémentée de diverses manières, notamment :  
  
-   Pages autonomes hébergées dans un navigateur Web.  
  
-   Pages compilées dans un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui est hébergé dans un navigateur Web.  
  
-   Pages compilées dans une application autonome et hébergées par une fenêtre de navigation \(<xref:System.Windows.Navigation.NavigationWindow>\).  
  
-   Pages hébergées par un cadre \(<xref:System.Windows.Controls.Frame>\) qui peut être hébergé dans une page autonome ou une page compilée dans un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ou une application autonome.  
  
 Pour faciliter la navigation, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implémente les éléments suivants :  
  
-   <xref:System.Windows.Navigation.NavigationService>, le moteur de navigation partagé pour traiter les requêtes de navigation utilisées par <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow> et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pour prendre en charge la navigation intra\-applications.  
  
-   Méthodes de navigation pour initialiser la navigation.  
  
-   Événements de navigation pour suivre et interagir avec la durée de vie de la navigation.  
  
-   Mémorisation de la navigation en avant et en arrière à l'aide d'un journal pouvant également être inspecté et manipulé.  
  
 Pour plus d'informations, consultez [Vue d'ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend également en charge un type spécial de navigation appelé « navigation structurée ».  La navigation structurée peut être utilisée pour appeler une ou plusieurs pages qui retournent des données de manière structurée et prédictible cohérente avec les appels de fonction.  Cette fonction dépend de la classe <xref:System.Windows.Navigation.PageFunction%601>, décrite plus loin dans [Vue d'ensemble de la navigation structurée](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  <xref:System.Windows.Navigation.PageFunction%601> permet également de simplifier la création de topologies de navigation complexes, décrites dans [Vue d'ensemble des topologies de navigation](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## Hébergement  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] peut être hébergé dans [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)], ou Firefox.  Chaque modèle d'hébergement possède son propre ensemble de considérations et de contraintes qui sont couvertes dans la rubrique [Hébergement](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## Génération et déploiement  
 Bien que des applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] simples puissent être générées à partir d'une invite de commandes utilisant des compilateurs de ligne de commande, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] s'intègre à [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] pour assurer une prise en charge supplémentaire qui simplifie le développement et le processus de génération.  Pour plus d'informations, consultez [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Selon le type d'application que vous générez, vous avez le choix entre une ou plusieurs options de déploiement.  Pour plus d'informations, consultez [Déploiement d'une application WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Vue d'ensemble de la gestion d'applications](../../../../docs/framework/wpf/app-development/application-management-overview.md)|Fournit une vue d'ensemble de la classe <xref:System.Windows.Application>, y compris la gestion de la durée de vie de l'application, des fenêtres, des ressources de l'application et de la navigation.|  
|[Fenêtres dans WPF](../../../../docs/framework/wpf/app-development/windows-in-wpf-applications.md)|Fournit des détails sur la gestion des fenêtres dans votre application, notamment la manière d'utiliser la classe <xref:System.Windows.Window> et les boîtes de dialogue.|  
|[Vue d'ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md)|Fournit une vue d'ensemble de la gestion de la navigation entre les pages de votre application.|  
|[Hébergement](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)|Fournit une vue d'ensemble de [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Génération et déploiement](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md)|Décrit comment générer et déployer votre application WPF.|  
|[Présentation de WPF dans Visual Studio 2015](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)|Décrit les principales fonctionnalités de WPF.|  
|[Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|Une procédure pas\-à\-pas qui indique comment créer une application WPF à l'aide de la navigation entre les pages, la structure, les contrôles, les images, les styles et la liaison.|