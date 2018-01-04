---
title: "Sécurité de confiance partielle de WPF"
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
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 745a5b87119bbce3211332eee9f23d80c15c9c28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-partial-trust-security"></a>Sécurité de confiance partielle de WPF
<a name="introduction"></a> En général, les applications Internet doivent disposer d’un accès direct limité aux ressources système critiques, afin d’éviter des dommages dus à des actes de malveillance. Par défaut, [!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] et langages de script côté client ne sont pas en mesure d’accéder aux ressources système critiques. Étant donné que [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] applications hébergées par le navigateur peuvent être lancées à partir du navigateur, elles doivent se conformer à un jeu de restrictions similaires. Pour appliquer ces restrictions, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] s’appuie sur les deux [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] et [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] (consultez [stratégie de sécurité de WPF - sécurité de la plate-forme](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Par défaut, les applications hébergées par le navigateur demandent la zone Internet [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] jeu d’autorisations, indépendamment de si elles sont lancées à partir d’Internet, intranet local ou l’ordinateur local. Les applications qui sont exécutées sans jeu d’autorisations complet sont exécutées avec une confiance dite partielle.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]fournit un large éventail de prise en charge pour garantir qu’autant de fonctionnalités que possible peut être utilisé en toute sécurité avec une confiance partielle et avec [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)], fournit la prise en charge supplémentaire pour la programmation de la confiance partielle.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Prise en charge de la confiance partielle avec des fonctionnalités WPF](#WPF_Feature_Partial_Trust_Support)  
  
-   [Programmation de la confiance partielle](#Partial_Trust_Programming)  
  
-   [Gestion des autorisations](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Prise en charge de la confiance partielle avec des fonctionnalités WPF  
 Le tableau suivant répertorie les principales fonctionnalités de [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] qui sont sécurisés à utiliser dans les limites du jeu d’autorisations de zone Internet.  
  
 Tableau 1 : Fonctionnalités WPF pouvant être utilisées en toute sécurité avec une confiance partielle  
  
|Domaine de fonctionnalités|Fonctionnalité|  
|------------------|-------------|  
|Général|Fenêtre du navigateur<br /><br /> Accès au site d’origine<br /><br /> IsolatedStorage (limité à 512 Ko)<br /><br /> Fournisseurs UIAutomation<br /><br /> Commandes<br /><br /> Éditeurs de méthode d’entrée (IME)<br /><br /> Stylet et entrée manuscrite<br /><br /> Glisser-déplacer simulé à l’aide d’événements de capture de la souris et de déplacement<br /><br /> OpenFileDialog<br /><br /> Désérialisation XAML (à l’aide de XamlReader.Load)|  
|Intégration web|Boîte de dialogue de téléchargement dans un navigateur<br /><br /> Navigation de premier niveau lancée par l’utilisateur<br /><br /> mailto:Links<br /><br /> Paramètres de l’URI (Uniform Resource Identifier)<br /><br /> HTTPWebRequest<br /><br /> Contenu WPF hébergé dans un IFRAME<br /><br /> Hébergement de pages HTML d’un même site à l’aide d’un Frame<br /><br /> Hébergement de pages HTML d’un même site à l’aide d’un WebBrowser<br /><br /> Services web (ASMX)<br /><br /> Services web (utilisant Windows Communication Foundation)<br /><br /> Scripts<br /><br /> DOM (Document Object Model)|  
|Objets visuels|2D et 3D<br /><br /> Animation<br /><br /> Média (site d’origine et interdomaines)<br /><br /> Images/Audio/Vidéo|  
|Lecture|FlowDocuments<br /><br /> Documents XPS<br /><br /> Polices système et incorporées<br /><br /> Polices CFF et TrueType|  
|Modification|Vérification de l’orthographe<br /><br /> RichTextBox<br /><br /> Prise en charge du Presse-papiers pour les entrées manuscrites et le texte en clair<br /><br /> Coller à l’initiative de l’utilisateur<br /><br /> Copie du contenu sélectionné|  
|Contrôles|Contrôles généraux|  
  
 Ce tableau décrit les [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] fonctionnalités à un niveau élevé. Pour plus d’informations, le [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] documente les autorisations qui sont requises par chaque membre dans [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. De plus, les fonctionnalités suivantes proposent des informations plus détaillées concernant l’exécution en mode confiance partielle, notamment des considérations spéciales.  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](consultez [vue d’ensemble du XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)).  
  
-   Les fenêtres contextuelles (voir <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
-   Glisser -déplacer (voir [Drag and Drop Overview](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)).  
  
-   Presse-papiers (voir <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
-   Création d’images (voir <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
-   Sérialisation (consultez <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
-   Ouvrez la boîte de dialogue de fichier (voir <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 Le tableau suivant décrit les [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jeu d’autorisations de zone de fonctionnalités qui ne sont pas sécurisées pour s’exécuter dans les limites d’Internet.  
  
 Tableau 2 : Fonctionnalités WPF ne pouvant pas être utilisées en toute sécurité avec une confiance partielle  
  
|Domaine de fonctionnalités|Fonctionnalité|  
|------------------|-------------|  
|Général|Fenêtre (boîtes de dialogue et fenêtres définies par l’application)<br /><br /> SaveFileDialog<br /><br /> Système de fichiers<br /><br /> Accès au Registre<br /><br /> Glisser-déposer<br /><br /> Sérialisation XAML (à l’aide de XamlWriter.Save)<br /><br /> Clients UIAutomation<br /><br /> Accès à la fenêtre source (HwndHost)<br /><br /> Prise en charge vocale intégrale<br /><br /> Interopérabilité Windows Forms|  
|Objets visuels|Effets bitmap<br /><br /> Encodage d’images|  
|Modification|Presse-papiers RTF (Rich Text Format)<br /><br /> Prise en charge XAML intégrale|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programmation de la confiance partielle  
 Pour [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] les applications, le code qui dépasse le jeu d’autorisations par défaut aura un comportement différent en fonction de la zone de sécurité. Dans certains cas, l’utilisateur reçoit un avertissement quand il tente de l’installer. Il peut choisir de continuer ou d’annuler l’installation. Le tableau suivant décrit le comportement de l’application pour chaque zone de sécurité et ce que vous devez faire pour que l’application reçoive la confiance totale.  
  
|Zone de sécurité|Comportement|Obtention de la confiance totale|  
|-------------------|--------------|------------------------|  
|Ordinateur local|Confiance totale automatique|Aucune action n’est nécessaire.|  
|Intranet et sites de confiance|Invite pour la confiance totale|Signez l’application XBAP avec un certificat afin que l’utilisateur consulte la source dans l’invite.|  
|Internet|Échec avec "Confiance non accordée"|Signez l’application XBAP avec un certificat.|  
  
> [!NOTE]
>  Le comportement décrit dans le tableau précédent concerne les applications XBAP de confiance totale qui ne suivent pas le modèle de déploiement approuvé ClickOnce.  
  
 En général, le code qui outrepasse les permissions autorisées est susceptible d’être du code commun qui est partagé entre des applications hébergées par le navigateur et des applications autonomes. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]et [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] offrent plusieurs techniques permettant de gérer ce scénario.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Détermination des autorisations à l’aide de la sécurité d’accès du code  
 Dans certaines situations, il est possible pour le code partagé dans des assemblys de bibliothèque peut être utilisé par les applications autonomes et [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Le code risque alors d’exécuter des fonctionnalités qui pourraient nécessiter plus d’autorisations que celles accordées par le jeu d’autorisations de l’application. Votre application peut déterminer si elle est certaines autorisations à l’aide de [!INCLUDE[TLA#tla_winfx](../../../includes/tlasharptla-winfx-md.md)] sécurité. Plus précisément, elle peut tester qu’il possède une autorisation spécifique en appelant le <xref:System.Security.CodeAccessPermission.Demand%2A> méthode sur l’instance de l’autorisation souhaitée. Ce test est illustré dans l’exemple suivant, dans lequel le code vérifie s’il peut enregistrer un fichier sur le disque local :  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Si une application ne possède pas l’autorisation souhaitée, l’appel à <xref:System.Security.CodeAccessPermission.Demand%2A> lève une exception de sécurité. Sinon, l’autorisation a été accordée. `IsPermissionGranted`encapsule ce comportement et retourne `true` ou `false` selon le cas.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Dégradation progressive des fonctionnalités  
 Pour du code qui peut être exécuté à partir de différentes zones, il est intéressant de pouvoir déterminer si une autorisation de faire ce qu’il a besoin de faire lui est accordée ou non. Même si la détermination de la zone est un élément, il est de loin préférable de proposer, si possible, une alternative à l’utilisateur. Par exemple, une application de confiance totale permet généralement aux utilisateurs de créer des fichiers où ils le souhaitent, alors qu’une application de confiance partielle peut créer des fichiers uniquement dans un stockage isolé. Si le code permettant de créer un fichier figure dans un assembly qui est partagé à la fois par des applications de confiance totale (autonomes) et des applications de confiance partielle (hébergées par le navigateur), et que les utilisateurs doivent pouvoir créer des fichiers dans ces deux types d’applications, le code partagé doit déterminer s’il est exécuté avec une confiance partielle ou totale avant de créer un fichier à l’emplacement approprié. Le code suivant illustre ces deux cas de figure.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Dans de nombreux cas, vous devez pouvoir trouver une alternative à la confiance partielle.  
  
 Dans un environnement contrôlé, tel qu’un intranet, les infrastructures managées personnalisées peuvent être installés sur le client de base dans le [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]. Ces bibliothèques peuvent exécuter du code qui requiert une confiance totale et être référencées à partir d’applications de confiance partielle uniquement à l’aide de <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (pour plus d’informations, consultez [sécurité](../../../docs/framework/wpf/security-wpf.md) et [sécurité WPF Stratégie de sécurité de la plateforme -](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Détermination de l’hôte de navigateur  
 À l’aide de [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] pour vérifier des autorisations est une technique appropriée lorsque vous devez vérifier sur une base par l’autorisation. Cette technique dépend toutefois de l’interception des exceptions dans le cadre d’un traitement normal, ce qui n’est généralement pas recommandé et peut entraîner des problèmes de performances. En revanche, si votre [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] exécute seulement dans le bac à sable de la zone Internet, vous pouvez utiliser la <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> propriété, qui retourne la valeur true pour [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>distingue uniquement si une application est en cours d’exécution dans un navigateur, pas le jeu d’autorisations d’une application est en cours d’exécution avec.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Gestion des autorisations  
 Par défaut, [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] s’exécutent en confiance partielle (jeu d’autorisations de la zone Internet par défaut). En fonction des spécifications de l’application, il est toutefois possible de changer le jeu d’autorisations par défaut. Par exemple, si un [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] est lancée à partir d’un intranet local, elle peut tirer parti d’un jeu d’autorisations plus, ce qui est indiqué dans le tableau suivant.  
  
 Tableau 3 : Autorisations LocalIntranet et Internet  
  
|Autorisation|Attribut|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Serveurs d’accès DNS|Oui|Non|  
|Variables d’environnement|Lecture|Oui|Non|  
|Boîtes de dialogue de fichiers|Ouvrir|Oui|Oui|  
|Boîtes de dialogue de fichiers|Non restreint|Oui|Non|  
|Stockage isolé|Isolement de l’assembly par utilisateur|Oui|Non|  
|Stockage isolé|Isolement inconnu|Oui|Oui|  
|Stockage isolé|Quota utilisateur illimité|Oui|Non|  
|Médias|Images, vidéo et audio sécurisés|Oui|Oui|  
|Impression|Impression par défaut|Oui|Non|  
|Impression|Impression sécurisée|Oui|Oui|  
|Réflexion|Émission|Oui|Non|  
|Sécurité|Exécution du code managé|Oui|Oui|  
|Sécurité|Déclarer des autorisations accordées|Oui|Non|  
|Interface utilisateur|Non restreint|Oui|Non|  
|Interface utilisateur|Fenêtres de niveau supérieur sécurisées|Oui|Oui|  
|Interface utilisateur|Presse-papiers personnel|Oui|Oui|  
|Navigateur web|Navigation de frame sécurisée vers HTML|Oui|Oui|  
  
> [!NOTE]
>  Le couper-coller est autorisé uniquement en mode confiance partielle quand il est à l’initiative de l’utilisateur.  
  
 Si vous devez augmenter le niveau d’autorisation, vous devez changer les paramètres du projet et le manifeste de l’application ClickOnce. Pour plus d’informations, consultez [Vue d’ensemble des applications de navigateur XAML](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md). Les documents suivants peuvent également être utiles.  
  
-   [Mage.exe (outil Manifest Generation and Editing)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe (outil Manifest Generation and Editing, client graphique)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [Sécurisation des applications ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Si votre [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] requiert une confiance totale, vous pouvez utiliser les mêmes outils pour élever les autorisations demandées. Bien qu’un [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] ne recevra une confiance totale si elle est installée sur lancé à partir de l’ordinateur local, l’intranet, ou d’une URL qui est répertoriée dans le navigateur sites fiables ou autorisés. Si l’application est installée à partir de l’intranet ou d’un site de confiance, l’utilisateur reçoit l’invite ClickOnce standard lui signalant les autorisations élevées. Il peut choisir de continuer ou d’annuler l’installation.  
  
 Vous pouvez également utiliser le modèle de déploiement approuvé ClickOnce pour le déploiement en mode confiance totale à partir de toute zone de sécurité. Pour plus d’informations, consultez [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) et [sécurité](../../../docs/framework/wpf/security-wpf.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité](../../../docs/framework/wpf/security-wpf.md)  
 [Stratégie de sécurité de WPF - sécurité de la plateforme](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Stratégie de sécurité de WPF - ingénierie de sécurité](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
