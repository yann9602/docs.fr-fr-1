---
title: "S&#233;curit&#233; (WPF) | Microsoft Docs"
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
  - "sécurité des applications (WPF)"
  - "sécurité des applications hébergées par un navigateur (WPF)"
  - "contrôles de fonctionnalités (WPF), sécurité"
  - "paramètres de sécurité Internet Explorer (WPF)"
  - "fichiers en XAML libre (WPF), comportement du bac à sable (sandbox)"
  - "sécurité de la navigation (WPF)"
  - "WebBrowser (contrôle WPF), sécurité"
  - "sécurité de WPF"
  - "fichiers XAML [WPF], comportement du bac à sable (sandbox)"
  - "sécurité des applications du navigateur XAML (WPF)"
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
caps.latest.revision: 38
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# S&#233;curit&#233; (WPF)
<a name="introduction"></a> Lors du développement d'applications hébergées par le navigateur et autonomes [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)], vous devez considérer le modèle de sécurité. Les applications autonomes [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] s'exécutent avec des autorisations illimitées \(jeu d'autorisations [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]**FullTrust**\), qu'elles soient déployées à l'aide de Windows Installer \(.msi\), XCopy ou [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  Le déploiement d'applications WPF de confiance partielle, autonomes, avec ClickOnce n'est pas pris en charge.  Toutefois, une application hôte de confiance totale peut créer un <xref:System.AppDomain> de confiance partielle à l'aide du modèle de complément .NET Framework.  Pour plus d'informations, consultez [Vue d'ensemble des compléments WPF](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Les applications hébergées par un navigateur [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] sont hébergées par [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] ou Firefox et peuvent être des [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] ou des documents [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] libre. Pour plus d'informations, consultez [Vue d'ensemble des applications de navigateur XAML](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 Les applications hébergées par un navigateur [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] s'exécutent par défaut dans un bac à sable \(sandbox\) de sécurité de confiance partielle, qui est limité au jeu d'autorisations de la zone **Internet** [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] par défaut.  Cela permet d'isoler efficacement les applications hébergées par un navigateur [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] de l'ordinateur client, de la même façon que pour des applications Web typiques.  Une XBAP peut élever des privilèges, jusqu'à la confiance totale, selon la zone de sécurité de l'URL de déploiement et la configuration de la sécurité du client.  Pour plus d'informations, consultez [Sécurité de confiance partielle de WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
 Cette rubrique décrit le modèle de sécurité des applications [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] autonomes et hébergées par un navigateur.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Navigation sécurisée](#SafeTopLevelNavigation)  
  
-   [Paramètres de sécurité du logiciel de navigation Web](#InternetExplorerSecuritySettings)  
  
-   [Contrôle WebBrowser et contrôles de fonctionnalités](#webbrowser_control_and_feature_controls)  
  
-   [Désactivation des assemblys APTCA pour les applications clientes d'un niveau de confiance partiel](#APTCA)  
  
-   [Comportement de bac à sable \(sandbox\) pour les fichiers XAML libre](#LooseContentSandboxing)  
  
-   [Ressources pour le développement des applications WPF qui encouragent la sécurité](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## Navigation sécurisée  
 Pour [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] distingue deux types de portées de navigation : l'application et le navigateur.  
  
 La *navigation dans l'application* est la navigation entre des éléments de contenu dans une application hébergée par un navigateur.  La *navigation dans un navigateur* est la navigation qui modifie le contenu et l'URL d'emplacement d'un navigateur lui\-même.  La relation entre la navigation dans l'application \(en général XAML\) et la navigation dans le navigateur \(en général HTML\) est affichée dans l'illustration suivante :  
  
 ![Diagramme de navigation](../../../docs/framework/wpf/media/safetoplevelnavigationfigure.png "SafeTopLevelNavigationFigure")  
  
 Le type de contenu considéré comme sécurisé pour la navigation à partir d'une application [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] dépend essentiellement du fait qu'il s'agisse d'une navigation dans une application ou dans un navigateur.  
  
<a name="Application_Navigation_Security"></a>   
### Sécurité de la navigation dans une application  
 La navigation dans une application est considérée comme sécurisée si elle peut être identifiée avec un [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack, qui prend en charge quatre types de contenu :  
  
|Content\-Type|Description|Exemple URI|  
|-------------------|-----------------|-----------------|  
|Ressource|Fichiers ajoutés à un projet avec un type de build **Ressource**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Contenu|Fichiers ajoutés à un projet avec un type de build **Contenu**.|`pack://application:,,,/MyContentFile.xaml`|  
|Site d'origine|Fichiers ajoutés à un projet avec un type de build **Aucun**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Code d'application|Ressources XAML qui ont un code\-behind compilé.<br /><br /> ou<br /><br /> Fichiers XAML ajoutés à un projet avec un type de build **Page**.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
>  Pour plus d'informations sur les fichiers de données d'application et les [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack, consultez [Fichiers de ressources, de contenu et de données d'une application WPF](../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 La navigation vers ces fichiers ayant ces types de contenu est possible via l'utilisateur ou par programmation :  
  
-   **Navigation utilisateur**.  L'utilisateur navigue en cliquant sur un élément <xref:System.Windows.Documents.Hyperlink>.  
  
-   **Navigation par programmation**.  L'application navigue sans impliquer l'utilisateur, par exemple, en définissant la propriété <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=fullName>.  
  
<a name="Browser_Navigation_Security"></a>   
### Sécurité de la navigation dans un navigateur  
 La navigation dans un navigateur est considérée comme sécurisée uniquement si les conditions suivantes sont respectées :  
  
-   **Navigation utilisateur**.  L'utilisateur navigue en cliquant sur un élément <xref:System.Windows.Documents.Hyperlink> qui est dans la <xref:System.Windows.Navigation.NavigationWindow> principale, et non dans un <xref:System.Windows.Controls.Frame> imbriqué.  
  
-   **Zone**.  Le contenu sur lequel porte la navigation se situe sur Internet ou un intranet local.  
  
-   **Protocole**.  Le protocole utilisé est **http**, **https**, **file** ou **mailto**.  
  
 Si une application [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] tente d'accéder au contenu sans respecter ces conditions, une exception <xref:System.Security.SecurityException> est levée.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## Paramètres de sécurité du logiciel de navigation Web  
 Les paramètres de sécurité sur votre ordinateur déterminent l'accès accordé à tout logiciel de navigation Web.  Le logiciel de navigation Web inclut toute application ou composant qui utilise le [WinINet \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179379) ou les API [UrlMon \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179383), notamment Internet Explorer et PresentationHost.exe.  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] est doté d'un mécanisme qui vous permet de configurer la fonctionnalité que vous pouvez exécuter dans ou à partir de [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], notamment :  
  
-   Composants appartenant au [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)]  
  
-   Contrôles et plug\-ins ActiveX  
  
-   Téléchargements  
  
-   Scripts  
  
-   Authentification utilisateur  
  
 La collection de fonctionnalités pouvant être sécurisée de cette façon est configurée pour chacune des zones suivantes : **Internet**, **Intranet**, **Sites de confiance** et **Sites sensibles**.  Les étapes suivantes décrivent comment configurer vos paramètres de sécurité :  
  
1.  Ouvrez le **Panneau de configuration**.  
  
2.  Cliquez sur **Réseau et Internet** puis sur **Options Internet**.  
  
     La boîte de dialogue Options Internet apparaît.  
  
3.  Sous l'onglet **Sécurité**, sélectionnez la zone pour laquelle les paramètres de sécurité seront configurés.  
  
4.  Cliquez sur le bouton **Personnaliser le niveau**.  
  
     La boîte de dialogue **Paramètres de sécurité** s'ouvre et vous pouvez configurer les paramètres de sécurité pour la zone sélectionnée.  
  
     ![Boîte de dialogue Paramètres de sécurité](../../../docs/framework/wpf/media/wpfsecurityfigure1.PNG "WPFSecurityFigure1")  
  
> [!NOTE]
>  Vous pouvez également arriver à la boîte de dialogue Options Internet à partir d'Internet Explorer.  Cliquez sur **Outils**, puis sur **Options Internet**.  
  
 À partir de [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], les paramètres de sécurité suivants sont inclus spécifiquement pour [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] :  
  
-   **XAML libre**.  Détermine si [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] peut accéder aux fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] et les libérer  \(options Activer, Désactiver et Demander\).  
  
-   **Applications du navigateur XAML**.  Détermine si [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] peut accéder aux fichiers [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] et les exécuter  \(options Activer, Désactiver et Demander\).  
  
 Par défaut, ces paramètres sont tous activés pour les zones **Internet**, **Intranet local** et **Sites de confiance** et désactivés pour la zone **Sites sensibles**.  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### Paramètres du Registre WPF relatifs à la sécurité  
 Outre les paramètres de sécurité disponibles via les Options Internet, les valeurs de Registre suivantes sont disponibles pour le blocage sélectif de plusieurs fonctionnalités WPF sensibles à la sécurité.  Les valeurs sont définies sous la clé suivante :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 Le tableau suivant décrit les différentes valeurs pouvant être utilisées.  
  
|Nom de la valeur|Type valeur|Données de la valeur|  
|----------------------|-----------------|--------------------------|  
|XBAPDisallow|REG\_DWORD|1 pour désactiver ; 0 pour activer.|  
|LooseXamlDisallow|REG\_DWORD|1 pour désactiver ; 0 pour activer.|  
|WebBrowserDisallow|REG\_DWORD|1 pour désactiver ; 0 pour activer.|  
|MediaAudioDisallow|REG\_DWORD|1 pour désactiver ; 0 pour activer.|  
|MediaImageDisallow|REG\_DWORD|1 pour désactiver ; 0 pour activer.|  
|MediaVideoDisallow|REG\_DWORD|1 pour désactiver ; 0 pour activer.|  
|ScriptInteropDisallow|REG\_DWORD|1 pour désactiver ; 0 pour activer.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## Contrôle WebBrowser et contrôles de fonctionnalités  
 Le contrôle <xref:System.Windows.Controls.WebBrowser> WPF peut être utilisé pour héberger le contenu Web.  Le contrôle <xref:System.Windows.Controls.WebBrowser> WPF encapsule le contrôle ActiveX WebBrowser sous\-jacent.  WPF fournit de la prise en charge pour la sécurisation de votre application lorsque vous utilisez le contrôle <xref:System.Windows.Controls.WebBrowser> WPF pour héberger le contenu Web non fiable.  Toutefois, certaines fonctionnalités de sécurité doivent être directement appliquées par les applications à l'aide du contrôle <xref:System.Windows.Controls.WebBrowser>.  Pour plus d'informations sur le contrôle ActiveX WebBrowser, consultez [Vues d'ensemble et didacticiels du contrôle WebBrowser \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Cette section s'applique également au contrôle <xref:System.Windows.Controls.Frame> puisqu'il utilise le <xref:System.Windows.Controls.WebBrowser> pour naviguer jusqu'au contenu HTML.  
  
 Si le contrôle WPF <xref:System.Windows.Controls.WebBrowser> est utilisé pour héberger le contenu Web non fiable, votre application doit utiliser un <xref:System.AppDomain> de confiance partielle pour permettre d'isoler votre code d'application du code de script HTML potentiellement nuisible.  Cela se vérifie tout particulièrement si votre application interagit avec le script hébergé à l'aide de la méthode <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> et de la propriété <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>.  Pour plus d'informations, consultez [Vue d'ensemble des compléments WPF](../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Si votre application utilise le contrôle <xref:System.Windows.Controls.WebBrowser> WPF, une autre méthode pour augmenter la sécurité et atténuer les attaques consiste à activer des contrôles de fonctionnalités Internet Explorer.  Les contrôles de fonctionnalités sont des ajouts à Internet Explorer qui permettent aux administrateurs et aux développeurs de configurer des fonctionnalités d'Internet Explorer et des applications qui hébergent le contrôle ActiveX WebBrowser, encapsulé par le contrôle <xref:System.Windows.Controls.WebBrowser> WPF.  Les contrôles de fonctionnalités peuvent être configurés à l'aide de la [fonction CoInternetSetFeatureEnabled \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179394) ou en modifiant les valeurs dans le Registre.  Pour plus d'informations sur les contrôles de fonctionnalités, consultez [Introduction aux contrôles de fonctionnalités \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179390) et [Contrôles de fonctionnalités Internet \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Si vous développez une application WPF autonome qui utilise le contrôle <xref:System.Windows.Controls.WebBrowser> WPF, WPF active automatiquement les contrôles de fonctionnalités suivants pour votre application.  
  
|Contrôle de fonctionnalité|  
|--------------------------------|  
|FEATURE\_MIME\_HANDLING|  
|FEATURE\_MIME\_SNIFFING|  
|FEATURE\_OBJECT\_CACHING|  
|FEATURE\_SAFE\_BINDTOOBJECT|  
|FEATURE\_WINDOW\_RESTRICTIONS|  
|FEATURE\_ZONE\_ELEVATION|  
|FEATURE\_RESTRICT\_FILEDOWNLOAD|  
|FEATURE\_RESTRICT\_ACTIVEXINSTALL|  
|FEATURE\_ADDON\_MANAGEMENT|  
|FEATURE\_HTTP\_USERNAME\_PASSWORD\_DISABLE|  
|FEATURE\_SECURITYBAND|  
|FEATURE\_UNC\_SAVEDFILECHECK|  
|FEATURE\_VALIDATE\_NAVIGATE\_URL|  
|FEATURE\_DISABLE\_TELNET\_PROTOCOL|  
|FEATURE\_WEBOC\_POPUPMANAGEMENT|  
|FEATURE\_DISABLE\_LEGACY\_COMPRESSION|  
|FEATURE\_SSLUX|  
  
 Puisque ces contrôles de fonctionnalités sont activés de manière non conditionnelle, ils peuvent affaiblir une application de confiance totale.  Dans ce cas, s'il n'existe aucun risque pour la sécurité de l'application spécifique et le contenu hébergé, le contrôle de fonctionnalité correspondant peut être désactivé.  
  
 Les contrôles de fonctionnalités sont appliqués par le processus qui instancie l'objet ActiveX WebBrowser.  Par conséquent, si vous créez une application autonome qui peut naviguer jusqu'à du contenu non fiable, vous devez sérieusement envisager d'activer des contrôles de fonctionnalités supplémentaires.  
  
> [!NOTE]
>  Cette recommandation est basée sur les recommandations générales pour la sécurité hôte de MSHTML et SHDOCVW.  Pour plus d'informations, consultez [FAQ sur la sécurité hôte de MSHTML : partie I sur II \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179396) et [FAQ sur la sécurité hôte de MSHTML : partie II sur II \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Pour votre fichier exécutable, envisagez d'activer les contrôles de fonctionnalités suivants en affectant 1 à la valeur de Registre.  
  
|Contrôle de fonctionnalité|  
|--------------------------------|  
|FEATURE\_ACTIVEX\_REPURPOSEDETECTION|  
|FEATURE\_BLOCK\_LMZ\_IMG|  
|FEATURE\_BLOCK\_LMZ\_OBJECT|  
|FEATURE\_BLOCK\_LMZ\_SCRIPT|  
|FEATURE\_RESTRICT\_RES\_TO\_LMZ|  
|FEATURE\_RESTRICT\_ABOUT\_PROTOCOL\_IE7|  
|FEATURE\_SHOW\_APP\_PROTOCOL\_WARN\_DIALOG|  
|FEATURE\_LOCALMACHINE\_LOCKDOWN|  
|FEATURE\_FORCE\_ADDR\_AND\_STATUS|  
|FEATURE\_RESTRICTED\_ZONE\_WHEN\_FILE\_NOT\_FOUND|  
  
 Pour votre fichier exécutable, envisagez de désactiver le contrôle de fonctionnalité suivant en affectant 0 à la valeur de Registre.  
  
|Contrôle de fonctionnalité|  
|--------------------------------|  
|FEATURE\_ENABLE\_SCRIPT\_PASTE\_URLACTION\_IF\_PROMPT|  
  
 Si vous exécutez une [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] de confiance partielle qui inclut un contrôle <xref:System.Windows.Controls.WebBrowser> WPF dans [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)], WPF héberge le contrôle ActiveX WebBrowser dans l'espace d'adressage du processus Internet Explorer.  Puisque le contrôle ActiveX WebBrowser est hébergé dans le processus [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], tous les contrôles de fonctionnalités pour Internet Explorer sont également activés pour le contrôle ActiveX WebBrowser.  
  
 Les XBAP qui fonctionnent dans Internet Explorer obtiennent également un niveau supplémentaire de sécurité en comparaison aux applications autonomes normales.  Cette sécurité supplémentaire est due au fait qu'Internet Explorer, et par conséquent le contrôle ActiveX WebBrowser, s'exécute en mode protégé par défaut sur [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] et [!INCLUDE[win7](../../../includes/win7-md.md)].  Pour plus d'informations sur le mode protégé, consultez [Connaissance et utilisation d'Internet Explorer en mode protégé \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Si vous essayez d'exécuter une XBAP qui inclut un contrôle <xref:System.Windows.Controls.WebBrowser> WPF dans Firefox tout en étant dans la zone Internet, une <xref:System.Security.SecurityException> sera levée.  Cela est dû à la stratégie de sécurité de WPF.  
  
<a name="APTCA"></a>   
## Désactivation des assemblys APTCA pour les applications clientes d'un niveau de confiance partiel  
 Lorsque des assemblys managés sont installés dans le [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)], ils sont tous d'un niveau de confiance suffisant puisque l'utilisateur doit fournir une autorisation pour les installer.  Comme ils ont un niveau de confiance suffisant, seules les applications clientes parfaitement fiables peuvent utiliser ces assemblys.  Pour autoriser les applications d'un niveau de confiance partiel à utiliser ces assemblys, ils doivent porter l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\).  Seuls les assemblys dont l'exécution dans des situations d'un niveau de confiance partiel a été testée doivent être marqués avec cet attribut.  
  
 Toutefois, il est possible qu'un assembly APTCA présente un défaut de sécurité après avoir été installé dans le [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)].  Lorsqu'un défaut de sécurité est détecté, les éditeurs de l'assembly peuvent fournir une mise à jour de sécurité pour résoudre le problème sur les installations existantes et pour protéger les installations réalisées après la détection du problème.  L'une des options de la mise à jour consiste à désinstaller l'assembly, bien que cela risque de bloquer d'autres applications clientes parfaitement fiables qui utilisent l'assembly.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] possède un mécanisme grâce auquel un assembly APTCA peut être désactivé pour les [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] d'un niveau de confiance partiel, sans désinstaller l'assembly APTCA.  
  
 Pour désactiver un assembly APTCA, vous devez créer une clé de Registre spéciale :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Voici un exemple :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Cette clé établit une entrée pour l'assembly APTCA.  Vous devez créer également une valeur dans cette clé qui active ou désactive l'assembly.  Les détails de cette valeur sont les suivants :  
  
-   Nom de la valeur : **APTCA\_FLAG**.  
  
-   Type valeur : **REG\_DWORD**.  
  
-   Données de la valeur : **1** pour désactiver ; **0** pour activer.  
  
 Si un assembly doit être désactivé pour les applications clientes d'un niveau de confiance partiel, vous pouvez écrire une mise à jour qui crée la clé de Registre et la valeur.  
  
> [!NOTE]
>  Les principaux assemblys [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] ne sont pas affectés par cette méthode de désactivation, puisqu'ils sont requis pour l'exécution des applications managées.  Le support technique pour la désactivation des assemblys APTCA cible essentiellement les applications tierces.  
  
<a name="LooseContentSandboxing"></a>   
## Comportement de bac à sable \(sandbox\) pour les fichiers XAML libre  
 Les fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libre sont des fichiers XAML de balisage uniquement qui ne dépendent pas d'un quelconque code\-behind, gestionnaire d'événements ou assembly spécifique à l'application.  Lorsque le navigateur accède directement à des fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libre, ces derniers sont chargés dans un bac à sable \(sandbox\) de sécurité par le jeu d'autorisations par défaut de la zone Internet.  
  
 Cependant, le comportement de sécurité est différent lorsqu'un <xref:System.Windows.Navigation.NavigationWindow> ou un <xref:System.Windows.Controls.Frame> dans une application autonome accède à ces fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libres.  
  
 Dans les deux cas, le fichier [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libre hérite des autorisations de son application hôte.  Du point de vue de la sécurité, ce comportement peut toutefois être indésirable, en particulier si le fichier [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libre a été généré par une entité inconnue ou non fiable.  Ce type de contenu est considéré comme du *contenu externe* et vous pouvez configurer <xref:System.Windows.Controls.Frame> et <xref:System.Windows.Navigation.NavigationWindow> pour qu'ils l'isolent.  Pour procéder à cet isolement, la propriété **SandboxExternalContent** doit avoir la valeur true, comme indiqué dans les exemples suivants pour <xref:System.Windows.Controls.Frame> et <xref:System.Windows.Navigation.NavigationWindow> :  
  
 [!code-xml[SecurityOverviewSnippets#FrameMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xml[SecurityOverviewSnippets#NavigationWindowMARKUP](../../../samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Lorsque ce paramètre est sélectionné, le contenu externe sera chargé dans un processus distinct de celui qui héberge l'application.  Ce processus est limité au jeu d'autorisations par défaut de la zone Internet, ce qui permet un isolement efficace de l'application d'hébergement et de l'ordinateur client.  
  
> [!NOTE]
>  Bien que la navigation des fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libres d'une <xref:System.Windows.Navigation.NavigationWindow> ou d'un <xref:System.Windows.Controls.Frame> dans une application autonome soit implémentée selon le navigateur WPF qui héberge l'infrastructure, impliquant le processus PresentationHost, le niveau de sécurité est légèrement inférieur au niveau du contenu chargé directement dans Internet Explorer sur [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] et [!INCLUDE[win7](../../../includes/win7-md.md)] \(lequel serait encore via PresentationHost\). Cela est dû au fait qu'une application WPF autonome utilisant un navigateur Web ne fournit pas la fonctionnalité de sécurité du mode protégé supplémentaire d'Internet Explorer.  
  
<a name="BestPractices"></a>   
## Ressources pour le développement des applications WPF qui encouragent la sécurité  
 Les quelques ressources supplémentaires suivantes fournissent de l'aide pour le développement des applications [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] qui encouragent la sécurité :  
  
|Zone|Ressource|  
|----------|---------------|  
|Code managé|[Aide sur la sécurité des modèles et des pratiques pour les applications \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=117426).|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[Sécurité d'accès du code](../../../docs/framework/misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[Sécurité et déploiement ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Sécurité de confiance partielle de WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)|  
  
## Voir aussi  
 [Sécurité de confiance partielle de WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)   
 [Stratégie de sécurité de WPF \- ingénierie de la plateforme](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)   
 [Stratégie de sécurité de WPF \- ingénierie de sécurité](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)   
 [Aide sur la sécurité des modèles et des pratiques pour les applications \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=117426)   
 [Sécurité d'accès du code](../../../docs/framework/misc/code-access-security.md)   
 [Sécurité et déploiement ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)