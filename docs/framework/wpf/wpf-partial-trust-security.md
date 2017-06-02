---
title: "S&#233;curit&#233; de confiance partielle de WPF | Microsoft Docs"
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
  - "déboguer des applications de confiance partielle"
  - "détecter les autorisations"
  - "conditions de sécurité des fonctionnalités"
  - "gérer les autorisations"
  - "applications de confiance partielle, débogage"
  - "sécurité de confiance partielle"
  - "permissions, détecter"
  - "permissions, gérer"
  - "paramètres de sécurité pour Internet Explorer"
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
caps.latest.revision: 40
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 36
---
# S&#233;curit&#233; de confiance partielle de WPF
<a name="introduction"></a> En règle générale, les applications Internet doivent disposer d'un accès direct limité aux ressources système critiques pour éviter des dégâts dus à des actes de malveillance.  Par défaut, le langage [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] et le langage de script côté client ne peuvent pas accéder à des ressources système critiques.  Comme les applications hébergées par le navigateur de [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] peuvent être lancées à partir du navigateur, elles doivent se conformer à un jeu de restrictions similaires.  Pour appliquer ces restrictions, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] s'appuie sur la [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] et sur [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] \(voir [Stratégie de sécurité de WPF \- ingénierie de la plateforme](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)\).  Par défaut, les applications hébergées par le navigateur requièrent le jeu d'autorisations [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] de la zone Internet, qu'elles aient été lancées à partir d'Internet, de l'intranet local ou de l'ordinateur local.  Les applications qui sont exécutées sans jeu d'autorisations complet sont exécutées avec une confiance dite partielle.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] assure de nombreuses prises en charge pour que le plus grand nombre possible de fonctionnalités puissent être utilisées en toute sécurité avec une confiance partielle et prend également en charge la programmation de la confiance partielle avec la [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)].  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Prise en charge de la confiance partielle avec des fonctionnalités WPF](#WPF_Feature_Partial_Trust_Support)  
  
-   [Programmation de la confiance partielle](#Partial_Trust_Programming)  
  
-   [Gestion des autorisations](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## Prise en charge de la confiance partielle avec des fonctionnalités WPF  
 Le tableau suivant présente les fonctionnalités de base de [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] qui peuvent être utilisées en toute sécurité dans le cadre du jeu d'autorisations de la zone Internet.  
  
 Tableau 1 : Fonctionnalités WPF pouvant être utilisées en toute sécurité avec une confiance partielle  
  
|Domaine de fonctionnalités|Fonctionnalité|  
|--------------------------------|--------------------|  
|Général|Fenêtre du navigateur<br /><br /> Accès au site d'origine<br /><br /> IsolatedStorage \(limité à 512 Ko\)<br /><br /> Fournisseurs UIAutomation<br /><br /> Commandes<br /><br /> Éditeurs de méthode d'entrée \(IME, Input Method Editor\)<br /><br /> Stylet et encre<br /><br /> Glisser\-déplacer simulé à l'aide d'événements de capture de la souris et de déplacement<br /><br /> OpenFileDialog<br /><br /> Désérialisation XAML \(via XamlReader.Load\)|  
|Intégration Web|Boîte de dialogue de téléchargement dans un navigateur<br /><br /> Navigation de niveau supérieur initiée par l'utilisateur<br /><br /> mailto:links<br /><br /> Paramètres de l'URI \(Uniform Resource Identifier\)<br /><br /> HTTPWebRequest<br /><br /> Contenu WPF hébergé dans un IFRAME<br /><br /> Hébergement de pages HTML sur le même site à l'aide d'un Frame<br /><br /> Hébergement de pages HTML sur le même site à l'aide d'un WebBrowser<br /><br /> Services Web \(ASMX\)<br /><br /> Services Web \(utilisant Windows Communication Foundation\)<br /><br /> Scripts<br /><br /> Document Object Model|  
|Objets visuels|2D et 3D<br /><br /> Animation<br /><br /> Média \(site d'origine et interdomaines\)<br /><br /> Images\/Audio\/Vidéo|  
|Lecture|FlowDocuments<br /><br /> Documents XPS<br /><br /> Polices système et incorporées<br /><br /> Polices CFF et TrueType|  
|Modification|Vérification de l'orthographe<br /><br /> RichTextBox<br /><br /> Prise en charge du Presse\-papiers pour l'encre et le texte brut<br /><br /> Coller initié par l'utilisateur<br /><br /> Copie du contenu sélectionné|  
|Contrôles|Contrôle généraux|  
  
 Ce tableau présente les fonctionnalités de base de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)].  Pour plus d'informations, le [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] documente les autorisations qui sont requises par chaque membre dans [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)].  En outre, les fonctionnalités suivantes proposent des informations plus détaillées sur l'exécution en mode confiance partielle, y compris des considérations spéciales.  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] \(voir [Vue d'ensemble du langage XAML \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)\).  
  
-   Menus contextuels \(voir <xref:System.Windows.Controls.Primitives.Popup?displayProperty=fullName>\).  
  
-   Glisser\-déplacer \(voir [Vue d'ensemble du glisser\-déplacer](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)\).  
  
-   Presse\-papiers \(voir <xref:System.Windows.Clipboard?displayProperty=fullName>\).  
  
-   Images \(voir <xref:System.Windows.Controls.Image?displayProperty=fullName>\).  
  
-   Sérialisation \(voir <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=fullName>\).  
  
-   Boîte de dialogue Ouvrir un fichier \(voir <xref:Microsoft.Win32.OpenFileDialog?displayProperty=fullName>\).  
  
 Les fonctionnalités [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ne pouvant pas être exécutées en toute sécurité dans le cadre du jeu d'autorisations de la zone Internet sont présentées dans le tableau suivant.  
  
 Tableau 2 : Fonctionnalités WPF ne pouvant pas être exécutées en toute sécurité avec une confiance partielle  
  
|Domaine de fonctionnalités|Fonctionnalité|  
|--------------------------------|--------------------|  
|Général|Fenêtre \(boîtes de dialogue et fenêtres définies par l'application\)<br /><br /> SaveFileDialog<br /><br /> Système de fichiers<br /><br /> Accès au Registre<br /><br /> Glisser\-déplacer<br /><br /> Sérialisation XAML \(via XamlWriter.Save\)<br /><br /> Clients UIAutomation<br /><br /> Accès à la fenêtre source \(HwndHost\)<br /><br /> Prise en charge vocale intégrale<br /><br /> Interopérabilité Windows Forms|  
|Objets visuels|Effets bitmap<br /><br /> Encodage d'images|  
|Modification|Presse\-papiers Rich Text Format<br /><br /> Prise en charge XAML intégrale|  
  
<a name="Partial_Trust_Programming"></a>   
## Programmation de la confiance partielle  
 Pour les applications [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)], le code qui dépasse le jeu d'autorisations par défaut aura un comportement différent selon la zone de sécurité.  Dans certains cas, l'utilisateur recevra un avertissement lorsqu'il essaie de l'installer.  L'utilisateur peut choisir de continuer ou d'annuler l'installation.  Le tableau suivant décrit le comportement de l'application pour chaque zone de sécurité et ce que vous devez faire pour que l'application reçoive la confiance totale.  
  
|Zone de sécurité|Comportement|Obtention de la confiance totale|  
|----------------------|------------------|--------------------------------------|  
|Ordinateur local|Confiance totale automatique|Aucune action n'est requise.|  
|Intranet et sites approuvés|Invite pour la confiance totale|Signez le XBAP avec un certificat afin que l'utilisateur consulte la source dans l'invite.|  
|Internet|Échecs avec « Confiance non accordée »|Signez l'application XBAP avec un certificat.|  
  
> [!NOTE]
>  Le comportement décrit dans le tableau précédent concerne les applications XBAP de confiance totale qui ne suivent pas le modèle de déploiement approuvé ClickOnce.  
  
 En général, le code qui outrepasse les permissions autorisées est souvent du code courant qui est partagé entre les applications hébergées par le navigateur et les applications autonomes.  [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] et [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] offrent plusieurs techniques pour la gestion de ce scénario.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### Détermination des autorisations à l'aide de la sécurité d'accès du code  
 Dans certains cas, le code partagé qui figure dans des assemblys de bibliothèque peut être utilisé par des applications autonomes et des applications [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)].  Le code risque alors d'exécuter des fonctionnalités qui pourraient requérir d'autres autorisations que celles accordées par le jeu d'autorisations de l'application.  Votre application peut déterminer si une autorisation donnée lui est accordée à l'aide de la sécurité [!INCLUDE[TLA#tla_winfx](../../../includes/tlasharptla-winfx-md.md)].  Elle peut plus particulièrement tester si une autorisation donnée lui est accordée en appelant la méthode <xref:System.Security.CodeAccessPermission.Demand%2A> sur l'instance de l'autorisation en question.  Cette vérification est illustrée dans l'exemple ci\-dessous, où le code vérifie s'il peut enregistrer un fichier sur le disque local :  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Lorsqu'une application ne dispose pas de l'autorisation souhaitée, l'appel à <xref:System.Security.CodeAccessPermission.Demand%2A> lève une exception de sécurité.  Sinon, l'autorisation a été accordée.  `IsPermissionGranted` encapsule ce comportement et retourne  `true` ou `false`.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### Dégradation progressive des fonctionnalités  
 Pour du code qui peut être exécuté à partir de différentes zones, il est intéressant de pouvoir déterminer si une autorisation de faire ce qu'il a besoin de faire lui est accordée ou non.  Même si la détermination de la zone est un élément, il est de loin préférable de proposer si possible une alternative à l'utilisateur.  Par exemple, une application de confiance totale permet généralement aux utilisateurs de créer des fichiers où bon leur semble, alors qu'une application de confiance partielle ne leur permet de créer des fichiers que dans le stockage isolé.  Si le code permettant de créer un fichier figure dans un assembly qui est partagé par une application de confiance totale \(autonome\) et une application de confiance partielle \(hébergée par le navigateur\), et que les utilisateurs doivent pouvoir créer des fichiers dans les deux applications, le code partagé doit déterminer s'il est exécuté avec une confiance partielle ou totale avant de créer un fichier à l'emplacement indiqué.  Le code suivant illustre ces deux cas de figure.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Dans de nombreux cas, vous devez pouvoir trouver une alternative à la confiance partielle.  
  
 Dans un environnement contrôlé, tel qu'un intranet, vous pouvez installer des infrastructures managées personnalisées sur la base cliente dans le [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)].  Ces bibliothèques peuvent exécuter du code qui requiert une confiance totale et être référencées à partir d'applications de confiance partielle uniquement à l'aide de <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(pour plus d'informations, consultez [Sécurité](../../../docs/framework/wpf/security-wpf.md) et [Stratégie de sécurité de WPF \- ingénierie de la plateforme](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)\).  
  
<a name="Browser_Host_Detection"></a>   
### Détermination de l'hôte de navigateur  
 L'utilisation de la [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] pour vérifier si des autorisations sont accordées est une technique indiquée lorsque vous devez effectuer des vérifications autorisation par autorisation.  Cette technique dépend toutefois de l'interception d'exceptions dans le cadre d'un traitement normal, ce qui n'est généralement pas recommandé et peut entraîner des problèmes de performances.  Si votre [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] est uniquement exécutée dans le bac à sable \(sandbox\) de la zone Internet, vous pouvez utiliser la propriété <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=fullName>, qui retourne la valeur true pour les [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  La propriété <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> peut uniquement déterminer si une application est exécutée dans un navigateur. Elle ne permet pas d'identifier le jeu d'autorisations avec lequel une application est exécutée.  
  
<a name="Managing_Permissions"></a>   
## Gestion des autorisations  
 Par défaut, les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] sont exécutées avec une confiance partielle \(jeu d'autorisations de la zone Internet par défaut\).  En fonction des besoins de l'application, il est toutefois possible de changer le jeu d'autorisations par défaut.  Par exemple, si une application [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] est lancée à partir d'un intranet local, elle peut alors bénéficier d'un jeu d'autorisations plus complet qui est indiqué dans le tableau ci\-dessous.  
  
 Tableau 3 : Autorisations LocalIntranet et Internet  
  
|Autorisation|Attribut|LocalIntranet|Internet|  
|------------------|--------------|-------------------|--------------|  
|DNS|Serveurs d'accès DNS|Oui|Non|  
|Variables d'environnement|Lecture|Oui|Non|  
|Boîtes de dialogue Fichier|Ouvrez .|Oui|Oui|  
|Boîtes de dialogue Fichier|Non restreint|Oui|Non|  
|Stockage isolé|Isolement de l'assembly par utilisateur|Oui|Non|  
|Stockage isolé|Isolement inconnu|Oui|Oui|  
|Stockage isolé|Quota utilisateur illimité|Oui|Non|  
|Multimédia|Audio, vidéo et images sécurisés|Oui|Oui|  
|Impression|Impression par défaut|Oui|Non|  
|Impression|Impression sécurisée|Oui|Oui|  
|Réflexion|Émission|Oui|Non|  
|Sécurité|Exécution du code managé|Oui|Oui|  
|Sécurité|Assertion des autorisations accordées|Oui|Non|  
|Interface utilisateur|Non restreint|Oui|Non|  
|Interface utilisateur|Fenêtres de niveau supérieur sécurisées|Oui|Oui|  
|Interface utilisateur|Propre Presse\-papiers|Oui|Oui|  
|Navigateur Web|Navigation de frame sécurisée vers HTML|Oui|Oui|  
  
> [!NOTE]
>  Le couper\-coller est autorisé uniquement en mode confiance partielle lorsqu'il est lancé par l'utilisateur.  
  
 Si vous devez augmenter le niveau d'autorisation, vous devez modifier les paramètres du projet et le manifeste de l'application ClickOnce.  Pour plus d'informations, consultez [Vue d'ensemble des applications de navigateur XAML](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  Les documents suivants peuvent également être utiles.  
  
-   [Mage.exe \(outil Manifest Generation and Editing\)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe \(outil Manifest Generation and Editing, client graphique\)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [Sécurisation des applications ClickOnce](../Topic/Securing%20ClickOnce%20Applications.md).  
  
 Si votre application [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] requiert une confiance totale, vous pouvez utiliser les mêmes outils pour élever les autorisations demandées.   Toutefois, une application [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] ne recevra une confiance totale que si elle est installée et lancée à partir de l'ordinateur local, de l'intranet ou d'une URL répertoriée dans les sites fiables ou autorisés du navigateur.  Si l'application est installée à partir de l'intranet ou d'un site fiable, l'utilisateur recevra l'invite ClickOnce standard lui signalant les autorisations élevées.  L'utilisateur peut choisir de continuer ou d'annuler l'installation.  
  
 Vous pouvez également utiliser le modèle de déploiement approuvé ClickOnce pour le déploiement en mode confiance totale à partir de toute zone de sécurité.  Pour plus d'informations, consultez [Vue d'ensemble du déploiement d'applications approuvées](../Topic/Trusted%20Application%20Deployment%20Overview.md) et [Sécurité](../../../docs/framework/wpf/security-wpf.md).  
  
## Voir aussi  
 [Sécurité](../../../docs/framework/wpf/security-wpf.md)   
 [Stratégie de sécurité de WPF \- ingénierie de la plateforme](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)   
 [Stratégie de sécurité de WPF \- ingénierie de sécurité](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)