---
title: Vue d'ensemble de la gestion d'applications
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
helpviewer_keywords: application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09129f2dc2bac2bb17ebacd6d6db020288b6f616
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="application-management-overview"></a>Vue d'ensemble de la gestion d'applications
Toutes les applications tendent à partager un jeu de fonctionnalités commun qui s’applique à l’implémentation et à la gestion. Cette rubrique fournit une vue d’ensemble des fonctionnalités de la <xref:System.Windows.Application> classe pour la création et la gestion des applications.  
   
  
## <a name="the-application-class"></a>Classe Application  
 Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], des fonctionnalités communes de portée application sont encapsulées dans le <xref:System.Windows.Application> classe. La <xref:System.Windows.Application> classe inclut les fonctionnalités suivantes :  
  
-   Suivi et interaction avec la durée de vie d’une application.  
  
-   Récupération et traitement des paramètres de ligne de commande.  
  
-   Détection et traitement des exceptions non gérées.  
  
-   Partage des propriétés de portée application et des ressources.  
  
-   Gestion des fenêtres dans des applications autonomes.  
  
-   Suivi et gestion de la navigation.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Comment effectuer des tâches courantes à l’aide de la classe Application  
 Si vous ne souhaitez pas tous les détails de la <xref:System.Windows.Application> (classe), le tableau suivant répertorie certaines des tâches courantes pour <xref:System.Windows.Application> et comment y répondre. En affichant l’API et les rubriques connexes, vous pouvez obtenir davantage d’informations et des exemples de code.  
  
|Tâche|Approche|  
|----------|--------------|  
|Obtenir un objet qui représente l’application actuelle|Utilisez la propriété <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>.|  
|Ajouter un écran de démarrage à une application|Consultez [ajouter un écran de démarrage pour une Application WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Démarrer une application|Utilisez la méthode <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType>.|  
|Arrêter une application|Utilisez le <xref:System.Windows.Application.Shutdown%2A> méthode de la <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> objet.|  
|Obtenir des arguments de la ligne de commande|Gérer les <xref:System.Windows.Application.Startup?displayProperty=nameWithType> événement et utilisez la <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> propriété. Pour obtenir un exemple, consultez la <xref:System.Windows.Application.Startup?displayProperty=nameWithType> événement.|  
|Obtenir et définir le code de sortie d’application|Définir le <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> propriété dans le <xref:System.Windows.Application.Exit?displayProperty=nameWithType> Gestionnaire d’événements ou appelez le <xref:System.Windows.Application.Shutdown%2A> méthode et passer un entier.|  
|Détecter et traiter des exceptions non gérées|Gérer les <xref:System.Windows.Application.DispatcherUnhandledException> événement.|  
|Obtenir et définir des ressources de portée application|Utilisez la propriété <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.|  
|Utiliser un dictionnaire de ressources de portée application|Consultez [utiliser un dictionnaire de ressources de portée Application](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md).|  
|Obtenir et définir les propriétés de portée application|Utilisez la propriété <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType>.|  
|Obtenir et enregistrer l’état d’une application|Consultez [conserver et restaurer les propriétés de l’étendue de l’Application entre les Sessions d’Application](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).|  
|Gérer les fichiers de données de non-code, dont les fichiers de ressources, les fichiers de contenu et les fichiers du site d’origine.|Consultez [ressource d’Application WPF, contenu et les fichiers de données](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).|  
|Gérer des fenêtres dans des applications autonomes|Consultez [WPF Windows Overview](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).|  
|Suivre et gérer la navigation|Consultez [vue d’ensemble de la Navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Définition d’application  
 Pour utiliser les fonctionnalités de la <xref:System.Windows.Application> (classe), vous devez implémenter une définition d’application. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] définition d’application est une classe qui dérive de <xref:System.Windows.Application> et est configuré avec un spécial [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] paramètre.  
  
### <a name="implementing-an-application-definition"></a>Implémentation d’une définition d’application  
 Un type [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] définition d’application est implémentée à l’aide de balisage et code-behind. Vous pouvez ainsi utiliser le balisage pour définir de façon déclarative les propriétés d’une application et les ressources ainsi que pour inscrire des événements, tout en gérant les événements et en implémentant le comportement spécifique à l’application dans un fichier code-behind.  
  
 L’exemple suivant montre comment implémenter une définition d’application à l’aide de balisage et de code-behind :  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Pour permettre l’interopérabilité d’un fichier de balisage et d’un fichier code-behind, les conditions suivantes doivent être satisfaites :  
  
-   Dans le balisage, la `Application` élément doit inclure le `x:Class` attribut. Lorsque l’application est générée, l’existence de `x:Class` dans le balisage de fichier entraîne [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] pour créer un `partial` classe qui dérive de <xref:System.Windows.Application> et porte le nom spécifié par le `x:Class` attribut. Cela requiert l’ajout d’un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] déclaration d’espace de noms pour le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schéma ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).  
  
-   Dans le code-behind, la classe doit être un `partial` classe portant le même nom que celui spécifié par le `x:Class` l’attribut dans le balisage et doit dériver de <xref:System.Windows.Application>. Cela permet au fichier code-behind à associer à la `partial` classe qui est généré pour le fichier de balisage lorsque l’application est générée (consultez [création d’une Application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Lorsque vous créez un projet d’Application WPF ou un projet d’Application de navigateur WPF à l’aide [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], une définition d’application est incluse par défaut et est définie à l’aide de balisage et code-behind.  
  
 Ce code est le minimum requis pour implémenter une définition d’application. Toutefois, un autre [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] configuration doit être effectuée à la définition d’application avant de générer et exécuter l’application.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Configuration de la définition d’application pour MSBuild  
 Applications autonomes et [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] requièrent l’implémentation d’un certain niveau d’infrastructure avant de pouvoir exécuter. La partie la plus importante de cette infrastructure est le point d’entrée. Quand une application est lancée par un utilisateur, le système d’exploitation appelle le point d’entrée, qui est une fonction connue pour démarrer les applications.  
  
 En règle générale, les développeurs ont toujours dû écrire eux-mêmes une partie ou l’intégralité de ce code, selon la technologie employée. Toutefois, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] génère ce code lorsque le fichier de balisage de votre définition d’application est configuré comme un [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` de l’élément, comme indiqué dans l’exemple suivant [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] fichier projet :  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 Étant donné que le fichier code-behind contient du code, il est marqué comme un [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` de l’élément, qui est normal.  
  
 L’application de ces [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] provoque des configurations pour les fichiers de balisage et code-behind d’une définition d’application [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] pour générer le code comme suit :  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 Le code résultant ajoute à votre définition d’application avec le code d’infrastructure supplémentaire, qui inclut la méthode de point d’entrée `Main`. Le <xref:System.STAThreadAttribute> attribut est appliqué à la `Main` méthode pour indiquer que le principal [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de thread pour le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application est un thread STA, qui est nécessaire pour [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications. Lorsqu’elle est appelée, `Main` crée une nouvelle instance de `App` avant d’appeler le `InitializeComponent` méthode pour enregistrer les événements et définir les propriétés qui sont implémentées dans le balisage. Étant donné que `InitializeComponent` est généré pour vous, vous n’avez pas besoin d’appeler explicitement `InitializeComponent` à partir d’une définition d’application comme vous le faites pour <xref:System.Windows.Controls.Page> et <xref:System.Windows.Window> implémentations. Enfin, le <xref:System.Windows.Application.Run%2A> méthode est appelée pour démarrer l’application.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Obtention de l’application actuelle  
 Étant donné que les fonctionnalités de la <xref:System.Windows.Application> classe sont partagés dans une application, il peut y avoir qu’une seule instance de la <xref:System.Windows.Application> classe par <xref:System.AppDomain>. Pour appliquer ceci, le <xref:System.Windows.Application> classe est implémentée comme une classe singleton (consultez [implémentation de Singleton en c#](http://go.microsoft.com/fwlink/?LinkId=100567)), qui crée une instance unique d’elle-même et fournit un accès partagé à avec le `static` <xref:System.Windows.Application.Current%2A> propriété.  
  
 Le code suivant montre comment acquérir une référence à la <xref:System.Windows.Application> objet en cours <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A>Retourne une référence à une instance de la <xref:System.Windows.Application> classe. Si vous souhaitez une référence à votre <xref:System.Windows.Application> dérivée de classe, vous devez effectuer un cast de la valeur de la <xref:System.Windows.Application.Current%2A> la propriété, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Vous pouvez inspecter la valeur de <xref:System.Windows.Application.Current%2A> à tout moment dans la durée de vie d’un <xref:System.Windows.Application> objet. Toutefois, vous devez être vigilant. Après le <xref:System.Windows.Application> classe est instancié, il existe une période pendant laquelle l’état de la <xref:System.Windows.Application> objet n’est pas cohérente. Pendant cette période, <xref:System.Windows.Application> effectue les diverses tâches d’initialisation qui sont requises par votre code à exécuter, notamment l’établissement de l’infrastructure d’application et définition des propriétés de l’inscription des événements. Si vous essayez d’utiliser le <xref:System.Windows.Application> de l’objet pendant cette période, votre code peut avoir des résultats inattendus, en particulier s’il dépend des diverses <xref:System.Windows.Application> définition des propriétés.  
  
 Lorsque <xref:System.Windows.Application> achève son initialisation, sa durée de vie commence réellement.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Durée de vie d’une application  
 La durée de vie d’un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application est marquée par plusieurs événements déclenchés par <xref:System.Windows.Application> pour vous avertir lorsque votre application a démarré, a été activé et désactivé et a été arrêté.  
  
  
<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Écran de démarrage  
 À compter de la [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], vous pouvez spécifier une image à utiliser dans une fenêtre de démarrage, ou *écran de démarrage*. La <xref:System.Windows.SplashScreen> classe facilite l’affichage d’une fenêtre de démarrage pendant le chargement de votre application. Le <xref:System.Windows.SplashScreen> fenêtre est créée et affichée avant <xref:System.Windows.Application.Run%2A> est appelée. Pour plus d’informations, consultez [temps de démarrage d’Application](../../../../docs/framework/wpf/advanced/application-startup-time.md) et [ajouter un écran de démarrage pour une Application WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Démarrage d’une application  
 Après avoir <xref:System.Windows.Application.Run%2A> est appelée et que l’application est initialisée, l’application est prête à s’exécuter. Ce moment est signifié le <xref:System.Windows.Application.Startup> événement est déclenché :  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 À ce stade dans la durée de vie d’une application, la plus courante consiste à afficher un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Showing_a_User_Interface"></a>   
### <a name="showing-a-user-interface"></a>Affichage d’une interface utilisateur  
 La plupart des autonome [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] applications ouvrir un <xref:System.Windows.Window> lorsqu’il démarre l’en cours d’exécution. Le <xref:System.Windows.Application.Startup> Gestionnaire d’événements est un emplacement à partir duquel vous pouvez effectuer, comme illustré dans le code suivant.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  Le premier <xref:System.Windows.Window> pour être instancié dans un autonome application devient la fenêtre principale de l’application par défaut. Cela <xref:System.Windows.Window> objet est référencé par le <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> propriété. La valeur de la <xref:System.Windows.Application.MainWindow%2A> propriété peut être modifiée par programme si une fenêtre différente de la première instancié <xref:System.Windows.Window> doit être la fenêtre principale.  
  
 Lorsqu’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] démarre en premier, il accèdera très probablement à un <xref:System.Windows.Controls.Page>. Ceci est illustré dans le code suivant.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Si vous gérez <xref:System.Windows.Application.Startup> à ouvrir uniquement un <xref:System.Windows.Window> ou accédez à un <xref:System.Windows.Controls.Page>, vous pouvez définir le `StartupUri` à la place l’attribut dans le balisage.  
  
 L’exemple suivant montre comment utiliser le <xref:System.Windows.Application.StartupUri%2A> à partir d’une application autonome pour ouvrir une <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 L’exemple suivant montre comment utiliser <xref:System.Windows.Application.StartupUri%2A> d’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pour accéder à un <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Ce balisage a le même effet que le code précédent pour ouvrir une fenêtre.  
  
> [!NOTE]
>  Pour plus d’informations sur la navigation, consultez [vue d’ensemble de la Navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 Vous devez gérer le <xref:System.Windows.Application.Startup> pour ouvrir un <xref:System.Windows.Window> si vous devez instancier à l’aide d’un constructeur par défaut, ou vous devez définir ses propriétés ou s’abonner à ses événements avant de les afficher, ou vous devez traiter tous les arguments de ligne de commande qui a été fourni lorsque l’application a été lancée.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Traitement des arguments de ligne de commande  
 Dans [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)], applications autonomes peuvent être lancées à partir d’une invite de commandes ou sur le bureau. Dans les deux cas, les arguments de ligne de commande peuvent être passés à l’application. L’exemple suivant montre une application qui est lancée avec un seul argument de ligne de commande, « /StartMinimized » :  
  
 `wpfapplication.exe /StartMinimized`  
  
 Pendant l’initialisation d’application, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] récupère les arguments de ligne de commande du système d’exploitation et les transmet à la <xref:System.Windows.Application.Startup> Gestionnaire d’événements via la <xref:System.Windows.StartupEventArgs.Args%2A> propriété de le <xref:System.Windows.StartupEventArgs> paramètre. Vous pouvez récupérer et stocker les arguments de ligne de commande à l’aide de code similaire au suivant.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Le code gère <xref:System.Windows.Application.Startup> pour vérifier si le **/StartMinimized** argument de ligne de commande a été fourni, dans ce cas, il ouvre la fenêtre principale avec un <xref:System.Windows.WindowState> de <xref:System.Windows.WindowState.Minimized>. Étant donné que la <xref:System.Windows.Window.WindowState%2A> propriété doit être définie par programme, le principal <xref:System.Windows.Window> doit être ouverte explicitement dans le code.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]ne peut pas récupérer et traiter des arguments de ligne de commande, car elles sont lancées à l’aide de [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] déploiement (voir [déploiement d’une Application WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)). En revanche, ils peuvent récupérer et traiter des paramètres de chaîne de requête à partir des URL servant à les lancer.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Activation et désactivation d’une application  
 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] permet aux utilisateurs de basculer entre les applications. La façon la plus courante consiste à utiliser la combinaison de touches ALT+TAB. Une application ne peut être basculée vers s’il a un visible <xref:System.Windows.Window> que l’utilisateur peut sélectionner. Actuellement sélectionné <xref:System.Windows.Window> est la *fenêtre active* (également connu sous le *fenêtre de premier plan*) et est le <xref:System.Windows.Window> qui reçoit l’entrée d’utilisateur. L’application à la fenêtre active est la *application active* (ou *application de premier plan*). Une application devient l’application active dans les circonstances suivantes :  
  
-   Elle est lancée et affiche un <xref:System.Windows.Window>.  
  
-   Un utilisateur bascule d’une autre application en sélectionnant un <xref:System.Windows.Window> dans l’application.  
  
 Vous pouvez détecter qu’une application devient active en gérant le <xref:System.Windows.Application.Activated?displayProperty=nameWithType> événement.  
  
 De même, une application peut devenir inactive dans les circonstances suivantes :  
  
-   Un utilisateur bascule vers une autre application à partir de l’application active.  
  
-   L’application s’arrête.  
  
 Vous pouvez détecter qu’une application est devenue inactive en gérant le <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> événement.  
  
 Le code suivant montre comment gérer les <xref:System.Windows.Application.Activated> et <xref:System.Windows.Application.Deactivated> événements afin de déterminer si une application est active.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 Un <xref:System.Windows.Window> peut également être activée et désactivée. Pour plus d'informations, consultez <xref:System.Windows.Window.Activated?displayProperty=nameWithType> et <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Ni <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ni <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> est déclenché pour [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Arrêt d’une application  
 La durée de vie d’une application s’achève quand elle est arrêtée, ce qui peut se produire pour les raisons suivantes :  
  
-   Un utilisateur ferme chaque <xref:System.Windows.Window>.  
  
-   Un utilisateur ferme le principal <xref:System.Windows.Window>.  
  
-   Un utilisateur met fin à la [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] session par session ou l’arrêt.  
  
-   Une condition spécifique à l’application a été remplie.  
  
 Pour vous aider à gérer l’arrêt de l’application, <xref:System.Windows.Application> fournit le <xref:System.Windows.Application.Shutdown%2A> (méthode), la <xref:System.Windows.Application.ShutdownMode%2A> propriété et le <xref:System.Windows.Application.SessionEnding> et <xref:System.Windows.Application.Exit> les événements.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A>peut uniquement être appelée à partir d’applications qui ont <xref:System.Security.Permissions.UIPermission>. Autonome [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications ont toujours cette autorisation. Toutefois, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] en cours d’exécution dans le bac à sable de la sécurité de confiance partielle de la zone Internet ne sont pas.  
  
#### <a name="shutdown-mode"></a>Mode d’arrêt  
 La plupart des applications s’arrêtent à la fermeture de toutes les fenêtres ou de la fenêtre principale. Toutefois, d’autres conditions spécifiques à l’application peuvent parfois déterminer l’arrêt d’une application. Vous pouvez spécifier les conditions dans lesquelles votre application s’arrête en définissant <xref:System.Windows.Application.ShutdownMode%2A> avec l’une des opérations suivantes <xref:System.Windows.ShutdownMode> valeurs d’énumération :  
  
-   <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 La valeur par défaut <xref:System.Windows.Application.ShutdownMode%2A> est <xref:System.Windows.ShutdownMode.OnLastWindowClose>, ce qui signifie qu’une application s’arrête automatiquement lorsque la dernière fenêtre de l’application est fermée par l’utilisateur. Toutefois, si votre application doit s’arrêter lorsque la fenêtre principale est fermée, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] qui effectue automatiquement si vous définissez <xref:System.Windows.Application.ShutdownMode%2A> à <xref:System.Windows.ShutdownMode.OnMainWindowClose>. L'exemple suivant le démontre.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Lorsque vous avez des conditions d’arrêt spécifiques à l’application, vous définissez <xref:System.Windows.Application.ShutdownMode%2A> à <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. Dans ce cas, il vous incombe d’arrêter une application en appelant explicitement la <xref:System.Windows.Application.Shutdown%2A> méthode ; sinon, votre application continue à s’exécuter même si toutes les fenêtres sont fermées. Notez que <xref:System.Windows.Application.Shutdown%2A> est appelée implicitement lorsque le <xref:System.Windows.Application.ShutdownMode%2A> est <xref:System.Windows.ShutdownMode.OnLastWindowClose> ou <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A>peut être définie à partir d’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], mais elle est ignorée ; un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est toujours arrêté quand elle est source de la navigation dans un navigateur ou lorsque le navigateur qui héberge le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est fermé. Pour plus d’informations, consultez [Vue d’ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
#### <a name="session-ending"></a>Fin de session  
 Les conditions d’arrêt qui sont décrits par le <xref:System.Windows.Application.ShutdownMode%2A> propriété sont spécifiques à une application. Dans certains cas, pourtant, une application peut s’arrêter à la suite d’une condition externe. La condition externe la plus courante se produit lorsqu’un utilisateur termine le [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] session par les actions suivantes :  
  
-   Déconnexion  
  
-   Arrêt  
  
-   Redémarrage  
  
-   Mise en veille prolongée  
  
 Pour détecter un [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] fin de la session, vous pouvez gérer le <xref:System.Windows.Application.SessionEnding> événement, comme illustré dans l’exemple suivant.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 Dans cet exemple, le code inspecte le <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> propriété pour déterminer comment la [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] session prend fin. Il utilise cette valeur pour afficher un message de confirmation à l’attention de l’utilisateur. Si l’utilisateur ne souhaite pas que la session se termine, le code définit <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> à `true` pour empêcher la [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] session à partir de la fin.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding>n’est pas déclenché pour [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
#### <a name="exit"></a>Exit  
 Quand une application s’arrête, il peut s’avérer nécessaire d’effectuer quelque traitement final, par exemple rendre persistant l’état de l’application. Pour ces situations, vous pouvez gérer le <xref:System.Windows.Application.Exit> événement.  
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 Pour obtenir un exemple complet, consultez [conserver et restaurer de portée Application propriétés entre les Sessions de l’Application](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit>peut être gérée par les applications autonomes et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Pour [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], <xref:System.Windows.Application.Exit> est déclenché dans les circonstances suivantes :  
  
-   Un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] utilisateur quitte.  
  
-   Dans [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], lorsque l’onglet qui héberge le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est fermé.  
  
-   Le navigateur est fermé.  
  
#### <a name="exit-code"></a>Code de sortie  
 Les applications sont principalement lancées par le système d’exploitation en réponse à une requête de l’utilisateur. Toutefois, une application peut être lancée par une autre application pour effectuer une tâche spécifique. Quand l’application lancée s’arrête, il est possible que l’application de lancement souhaite connaître la condition dans laquelle s’est effectué cet arrêt. Dans ces situations, [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] permet aux applications de retourner un code de sortie d’application à l’arrêt. Par défaut, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications retournent une valeur de code de sortie de 0.  
  
> [!NOTE]
>  Lorsque vous déboguez à partir de [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], le code de sortie d’application s’affiche dans le **sortie** fenêtre lorsque l’application s’arrête, dans un message qui ressemble à ce qui suit :  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Vous ouvrez le **sortie** fenêtre en cliquant sur **sortie** sur la **vue** menu.  
  
 Pour modifier le code de sortie, vous pouvez appeler la <xref:System.Windows.Application.Shutdown%28System.Int32%29> surcharge qui accepte un argument entier soit le code de sortie :  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Vous pouvez détecter la valeur de code de sortie et remplacez-la par la gestion de la <xref:System.Windows.Application.Exit> événement. Le <xref:System.Windows.Application.Exit> Gestionnaire d’événements reçoit un <xref:System.Windows.ExitEventArgs> qui fournit l’accès au code de sortie avec la <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> propriété. Pour plus d'informations, consultez <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Vous pouvez définir le code de sortie dans les applications autonomes et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Toutefois, la valeur de code de sortie est ignorée pour [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Exceptions non gérées  
 Il peut parfois arriver qu’une application s’arrête anormalement, par exemple en cas d’exception inattendue. Dans ce cas, il est possible qu’elle n’ait pas le code nécessaire à la détection et au traitement de l’exception. Ce type d’exception est une exception non gérée ; une notification similaire à celle illustrée dans la figure ci-dessous s’affiche avant la fermeture de l’application.  
  
 ![Notification d’exception non gérée](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 Du point de vue de l’expérience utilisateur, il est préférable pour une application d’éviter ce comportement par défaut en effectuant certaines ou l’ensemble des opérations suivantes :  
  
-   Affichage d’informations conviviales.  
  
-   Tentative de maintenir une application en cours d’exécution.  
  
-   L’enregistrement des informations détaillées, conviviales et des exceptions dans les [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] journal des événements.  
  
 Implémentation de cette prise en charge dépend de qui est en mesure de détecter les exceptions non gérées, qui est ce que le <xref:System.Windows.Application.DispatcherUnhandledException> événement est déclenché pour.  
  
 [!code-xaml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 Le <xref:System.Windows.Application.DispatcherUnhandledException> Gestionnaire d’événements reçoit un <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> paramètre qui contient des informations contextuelles concernant l’exception non gérée, y compris l’exception proprement dit (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Vous pouvez utiliser ces informations pour déterminer comment gérer l’exception.  
  
 Lorsque vous gérez <xref:System.Windows.Application.DispatcherUnhandledException>, vous devez définir le <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> propriété `true`; sinon, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] toujours considère que l’exception non gérée et rétablit le comportement par défaut décrit précédemment. Si une exception non gérée est levée et la <xref:System.Windows.Application.DispatcherUnhandledException> événement n’est pas géré, ou l’événement est géré et <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> a la valeur `false`, l’application s’arrête immédiatement. En outre, aucun autre <xref:System.Windows.Application> sont déclenchés. Par conséquent, vous devez gérer <xref:System.Windows.Application.DispatcherUnhandledException> si votre application comporte du code qui doit s’exécuter avant l’arrêt de l’application.  
  
 Bien qu’une application puisse s’arrêter à la suite d’une exception non gérée, elle s’arrête habituellement en réponse à une requête de l’utilisateur, comme décrit dans la section suivante.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Événements de durée de vie de l'application  
 Applications autonomes et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] n’avez pas exactement la même durée de vie. La figure suivante illustre les principaux événements de la durée de vie d’une application autonome et indique l’ordre dans lequel ils sont déclenchés.  
  
 ![Application autonome &#45; Événements d’objets d’application](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 De même, la figure suivante illustre les principaux événements dans la durée de vie d’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]et indique l’ordre dans lequel ils sont déclenchés.  
  
 ![XBAP &#45; Événements d’objets d’application](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Application>  
 [Vue d'ensemble des fenêtres WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)  
 [Vue d’ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [Fichiers de ressources, de contenu et de données d’une application WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)  
 [URI à en-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Modèle d’application : Les rubriques de procédures](http://msdn.microsoft.com/en-us/76771b09-3688-4d1c-8818-9b3f4cf39a30)  
 [Développement de l’application](../../../../docs/framework/wpf/app-development/index.md)
