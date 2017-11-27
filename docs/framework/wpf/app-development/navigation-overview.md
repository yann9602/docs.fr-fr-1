---
title: Vue d'ensemble de la navigation
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
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
caps.latest.revision: "69"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73bb3a2f43c5bd91d7a107a0a053381ca7bc0559
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="navigation-overview"></a>Vue d'ensemble de la navigation
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]prend en charge la navigation de style navigateur qui peut être utilisée dans les deux types d’applications : applications autonomes et [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]. Pour le contenu du package pour la navigation, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit la <xref:System.Windows.Controls.Page> classe. Vous pouvez naviguer à partir d’un <xref:System.Windows.Controls.Page> à l’autre de façon déclarative, en utilisant un <xref:System.Windows.Documents.Hyperlink>, ou par programme, en utilisant le <xref:System.Windows.Navigation.NavigationService>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise le journal pour se souvenir des pages visitées et y revenir.  
  
 <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, et le journal forment le cœur de la prise en charge de navigation offerte par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Cette vue d’ensemble explore ces fonctionnalités en détail avant de couvrir la prise en charge de la navigation avancée qui inclut la navigation libres [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichiers [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] fichiers et des objets.  
  
> [!NOTE]
>  Dans cette rubrique, le terme « navigateur » fait uniquement référence aux navigateurs qui peuvent héberger [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] les applications qui incluent actuellement [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] et Firefox. Cas spécifiques [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fonctionnalités sont prises en charge uniquement par un navigateur particulier, la version du navigateur est appelée.  
   
     
## <a name="navigation-in-wpf-applications"></a>Navigation dans les applications WPF  
 Cette rubrique fournit une vue d’ensemble des fonctionnalités de navigation de clé dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ces fonctionnalités sont disponibles pour les applications autonomes et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bien que cette rubrique présente les dans le contexte d’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
> [!NOTE]
>  Cette rubrique n’explique pas comment générer et déployer [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Pour plus d’informations sur [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], consultez [vue d’ensemble des Applications de navigateur XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
 Cette section explique et illustre les aspects suivants de la navigation :  
  
-   [Implémentation d’une page](#CreatingAXAMLPage)  
  
-   [Configuration d’une page de démarrage](#Configuring_a_Start_Page)  
  
-   [Configuration du titre, de la largeur et de la hauteur de la fenêtre hôte](#ConfiguringAXAMLPage)  
  
-   [Navigation par lien hypertexte](#NavigatingBetweenXAMLPages)  
  
-   [Navigation vers un fragment](#FragmentNavigation)  
  
-   [Service de navigation](#NavigationService)  
  
-   [Navigation par programmation avec le service de navigation](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [Durée de vie de la navigation](#Navigation_Lifetime)  
  
-   [Mémorisation de la navigation avec le journal](#NavigationHistory)  
  
-   [Durée de vie d’une page et le journal](#PageLifetime)  
  
-   [Conservation de l’état du contenu avec l’historique de navigation](#RetainingContentStateWithNavigationHistory)  
  
-   [Cookies](#Cookies)  
  
-   [Navigation structurée](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>Implémentation d’une page  
 Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vous pouvez accéder à plusieurs types de contenu qui incluent [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] objets, les objets personnalisés, les valeurs d’énumération, les contrôles utilisateur, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichiers, et [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] fichiers. Toutefois, vous découvrirez que la façon la plus courante et pratique pour le contenu du package est à l’aide de <xref:System.Windows.Controls.Page>. En outre, <xref:System.Windows.Controls.Page> implémente des fonctionnalités spécifiques à la navigation pour améliorer leur apparence et simplifier le développement.  
  
 À l’aide de <xref:System.Windows.Controls.Page>, vous pouvez implémenter de façon déclarative une page navigable de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] contenu à l’aide de balisage comme suit.  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A <xref:System.Windows.Controls.Page> qui est implémentée dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] balisage a `Page` comme élément racine et requiert le [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] déclaration d’espace de noms. Le `Page` élément contient le contenu que vous souhaitez accéder à et afficher. Vous ajoutez du contenu en définissant le `Page.Content` élément de propriété, comme indiqué dans le balisage suivant.  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` ne peut contenir qu’un seul élément enfant. Dans l’exemple précédent, le contenu est une chaîne unique, « Hello, Page! » Dans la pratique, vous utiliserez généralement un contrôle de disposition comme élément enfant (consultez [disposition](../../../../docs/framework/wpf/advanced/layout.md)) pour contenir et composer votre contenu.  
  
 Les éléments enfants d’un `Page` élément sont considérées comme le contenu d’un <xref:System.Windows.Controls.Page> et, par conséquent, vous n’avez pas besoin d’utiliser explicites `Page.Content` déclaration. Le balisage suivant est l’équivalent déclaratif de l’exemple précédent.  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 Dans ce cas, `Page.Content` est défini automatiquement avec les éléments enfants de le `Page` élément. Pour plus d’informations, consultez [Modèle de contenu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
 Balisage seule <xref:System.Windows.Controls.Page> est utile pour afficher le contenu. Toutefois, un <xref:System.Windows.Controls.Page> peut également afficher les contrôles qui permettent aux utilisateurs d’interagir avec la page, et il peut répondre à une interaction utilisateur par la gestion des événements et en appelant la logique d’application. Interactif <xref:System.Windows.Controls.Page> est implémentée à l’aide d’une combinaison de balisage et code-behind, comme indiqué dans l’exemple suivant.  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 Pour permettre à un fichier de balisage et un fichier code-behind de fonctionner ensemble, la configuration suivante est nécessaire :  
  
-   Dans le balisage, la `Page` élément doit inclure le `x:Class` attribut. Lorsque l’application est générée, l’existence de `x:Class` dans le balisage de fichier entraîne [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] pour créer un `partial` classe qui dérive de <xref:System.Windows.Controls.Page> et porte le nom spécifié par le `x:Class` attribut. Cela requiert l’ajout d’un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] déclaration d’espace de noms pour le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schéma ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Le texte généré `partial` la classe implémente `InitializeComponent`, qui est appelé pour enregistrer les événements et définir les propriétés qui sont implémentées dans le balisage.  
  
-   Dans le code-behind, la classe doit être un `partial` classe portant le même nom que celui spécifié par le `x:Class` attribut dans le balisage et elle doit dériver de <xref:System.Windows.Controls.Page>. Cela permet au fichier code-behind à associer à la `partial` classe qui est généré pour le fichier de balisage lorsque l’application est générée (consultez [création d’une Application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
-   Dans le code-behind, le <xref:System.Windows.Controls.Page> classe doit implémenter un constructeur qui appelle le `InitializeComponent` (méthode). `InitializeComponent`est implémentée par le balisage générée du fichier `partial` classe pour enregistrer les événements et définir les propriétés qui sont définies dans le balisage.  
  
> [!NOTE]
>  Lorsque vous ajoutez un nouveau <xref:System.Windows.Controls.Page> dans votre projet en utilisant [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], le <xref:System.Windows.Controls.Page> est implémentée à l’aide de balisage et code-behind, et il inclut la configuration nécessaire pour créer l’association entre les fichiers de balisage et code-behind en tant que décrites ici.  
  
 Une fois que vous avez un <xref:System.Windows.Controls.Page>, vous pouvez naviguer jusqu'à lui. Pour spécifier la première <xref:System.Windows.Controls.Page> qu’une application accède à, vous devez configurer le démarrage <xref:System.Windows.Controls.Page>.  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>Configuration d’une page de démarrage  
 Les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nécessitent l’hébergement d’une certaine quantité d’infrastructure d’application dans un navigateur. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], le <xref:System.Windows.Application> classe fait partie d’une définition d’application qui établit l’infrastructure d’application requise (consultez [vue d’ensemble de la gestion des applications](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
 Une définition d’application est généralement implémentée à l’aide de balisage et code-behind, avec le fichier de balisage configuré comme un [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` élément. Voici une définition d’application pour un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 Un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] peut utiliser sa définition d’application pour spécifier un point de départ <xref:System.Windows.Controls.Page>, qui est la <xref:System.Windows.Controls.Page> qui est automatiquement chargé quand le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est lancée. Pour cela, définissez la <xref:System.Windows.Application.StartupUri%2A> propriété avec le [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] pour souhaité <xref:System.Windows.Controls.Page>.  
  
> [!NOTE]
>  Dans la plupart des cas, le <xref:System.Windows.Controls.Page> est compilée dans ou déployée avec une application. Dans ce cas, le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui identifie un <xref:System.Windows.Controls.Page> est un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], qui est un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui est conforme à la *pack* schéma. Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] sont décrites plus en détail dans [URI à en-tête Pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md). Vous pouvez également naviguer vers du contenu à l’aide du schéma http, comme indiqué ci-dessous.  
  
 Vous pouvez définir <xref:System.Windows.Application.StartupUri%2A> façon déclarative dans le balisage, comme illustré dans l’exemple suivant.  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 Dans cet exemple, le `StartupUri` attribut est défini avec un pack relatif [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui identifie HomePage.xaml. Lorsque le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est lancé, HomePage.xaml est automatiquement navigué vers et affichées. Cela est illustré par la figure suivante, qui montre un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui a été lancé à partir d’un serveur Web.  
  
 ![Page XBAP](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure9.png "NavigationOverviewFigure9")  
  
> [!NOTE]
>  Pour plus d’informations sur le développement et le déploiement de [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], consultez [vue d’ensemble des Applications de navigateur XAML WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md) et [déploiement d’une Application WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>Configuration du titre, de la largeur et de la hauteur de la fenêtre hôte  
 Vous aurez peut-être remarqué dans l’illustration précédente est que le titre du navigateur et du volet d’onglets est la [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. En plus d’être long, le titre n’est ni attrayant, ni informatif. Pour cette raison, <xref:System.Windows.Controls.Page> offre un moyen de modifier le titre en définissant le <xref:System.Windows.Controls.Page.WindowTitle%2A> propriété. En outre, vous pouvez configurer la largeur et la hauteur de la fenêtre du navigateur en définissant <xref:System.Windows.Controls.Page.WindowWidth%2A> et <xref:System.Windows.Controls.Page.WindowHeight%2A>, respectivement.  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, et <xref:System.Windows.Controls.Page.WindowHeight%2A> peut être définie de façon déclarative dans le balisage, comme illustré dans l’exemple suivant.  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 Le résultat est affiché dans l’illustration suivante.  
  
 ![Titre, hauteur, largeur de la fenêtre](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure2.png "NavigationOverviewFigure2")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>Navigation par lien hypertexte  
 Un type [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] comprend plusieurs pages. Le plus simple pour naviguer d’une page à une autre consiste à utiliser un <xref:System.Windows.Documents.Hyperlink>. Vous pouvez ajouter de façon déclarative un <xref:System.Windows.Documents.Hyperlink> à un <xref:System.Windows.Controls.Page> à l’aide de la `Hyperlink` élément, qui est indiqué dans le balisage suivant.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A `Hyperlink` élément requiert les éléments suivants :  
  
-   Le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la <xref:System.Windows.Controls.Page> à atteindre, comme spécifié par le `NavigateUri` attribut.  
  
-   Contenu qu’un utilisateur peut cliquer pour lancer le volet de navigation, tels que le texte et des images (pour le contenu qui le `Hyperlink` élément peut contenir, consultez <xref:System.Windows.Documents.Hyperlink>).  
  
 L’illustration suivante montre un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] avec un <xref:System.Windows.Controls.Page> qui a un <xref:System.Windows.Documents.Hyperlink>.  
  
 ![Page avec lien hypertexte](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure3.png "NavigationOverviewFigure3")  
  
 Comme pour tout, en cliquant sur le <xref:System.Windows.Documents.Hyperlink> provoque la [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pour accéder à la <xref:System.Windows.Controls.Page> qui est identifié par le `NavigateUri` attribut. En outre, le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ajoute une entrée pour la précédente <xref:System.Windows.Controls.Page> à la liste de Pages récentes dans [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Ce cas est illustré dans la figure suivante.  
  
 ![Boutons Précédent et Suivant](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 Ainsi que la prise en charge de la navigation à partir d’un <xref:System.Windows.Controls.Page> vers un autre, <xref:System.Windows.Documents.Hyperlink> également prend en charge la navigation vers un fragment.  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>Navigation vers un fragment  
 *Navigation vers un fragment* est la navigation vers un fragment de contenu, que ce soit en cours <xref:System.Windows.Controls.Page> ou un autre <xref:System.Windows.Controls.Page>. Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], un fragment de contenu est le contenu qui est contenu dans un élément nommé. Un élément nommé est un élément qui a son `Name` ensemble d’attributs. La balise suivante montre un jeu nommé `TextBlock` élément qui contient un fragment de contenu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 Pour un <xref:System.Windows.Documents.Hyperlink> pour accéder à un fragment de contenu, le `NavigateUri` attribut doit inclure les éléments suivants :  
  
-   Le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la <xref:System.Windows.Controls.Page> avec le fragment de contenu à atteindre.  
  
-   un caractère "#" ;  
  
-   Le nom de l’élément sur le <xref:System.Windows.Controls.Page> qui contient le fragment de contenu.  
  
 Un fragment [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] a le format suivant.  
  
 *URIPage* `#` *NomÉlément*  
  
 L’exemple suivant montre un exemple d’un `Hyperlink` qui est configuré pour accéder à un fragment de contenu.  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  Cette section décrit l’implémentation de navigation de fragment par défaut dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]vous permet également d’implémenter votre propre schéma de navigation de fragment qui, en partie, nécessite un traitement le <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> événement.  
  
> [!IMPORTANT]
>  Vous pouvez accéder à des fragments dans libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages (balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] avec les fichiers `Page` comme élément racine) uniquement si les pages peuvent être parcourus [!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)].  
>   
>  Toutefois, un faible [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page peut naviguer vers ses propres fragments.  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>Service de navigation  
 Alors que <xref:System.Windows.Documents.Hyperlink> permet à un utilisateur initialiser la navigation vers un particulier <xref:System.Windows.Controls.Page>, le travail de localisation et de téléchargement de la page est effectué par la <xref:System.Windows.Navigation.NavigationService> classe. Essentiellement, <xref:System.Windows.Navigation.NavigationService> offre la possibilité de traiter une demande de navigation pour le compte du code client, telles que le <xref:System.Windows.Documents.Hyperlink>. En outre, <xref:System.Windows.Navigation.NavigationService> implémente la prise en charge de niveau supérieur pour suivre et influencer une requête de navigation.  
  
 Lorsqu’un <xref:System.Windows.Documents.Hyperlink> est activé, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] appelle <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> pour localiser et télécharger le <xref:System.Windows.Controls.Page> dans le pack spécifié [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Téléchargé <xref:System.Windows.Controls.Page> est convertie en une arborescence d’objets dont l’objet racine est une instance de téléchargé <xref:System.Windows.Controls.Page>. Une référence à la racine <xref:System.Windows.Controls.Page> objet est stocké dans le <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> propriété. Le Pack de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour le contenu cible de la navigation est stocké dans le <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> propriété, alors que le <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> stocke le Pack de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la dernière page qui a été utilisée.  
  
> [!NOTE]
>  Il est possible pour un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application à avoir plusieurs active <xref:System.Windows.Navigation.NavigationService>. Pour plus d’informations, consultez [hôtes de Navigation](#Navigation_Hosts) plus loin dans cette rubrique.  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>Navigation par programmation avec le service de navigation  
 Vous n’avez pas besoin de connaître <xref:System.Windows.Navigation.NavigationService> si la navigation est implémentée de façon déclarative dans le balisage à l’aide <xref:System.Windows.Documents.Hyperlink>, car <xref:System.Windows.Documents.Hyperlink> utilise le <xref:System.Windows.Navigation.NavigationService> à votre place. Cela signifie que, tant que le parent direct ou indirect d’un <xref:System.Windows.Documents.Hyperlink> est un hôte de navigation (consultez [hôtes de Navigation](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> sera en mesure de trouver et utiliser le service de navigation de l’hôte de navigation pour traiter un demande de navigation.  
  
 Toutefois, il existe des cas où vous devez utiliser <xref:System.Windows.Navigation.NavigationService> directement, notamment les suivantes :  
  
-   Lorsque vous devez instancier un <xref:System.Windows.Controls.Page> à l’aide d’un constructeur par défaut.  
  
-   Lorsque vous devez définir des propriétés sur le <xref:System.Windows.Controls.Page> avant de vous y rendre.  
  
-   Lorsque le <xref:System.Windows.Controls.Page> que doit être la cible de la navigation ne peut être déterminée au moment de l’exécution.  
  
 Dans ces situations, vous devez écrire du code pour initialiser la navigation par programmation en appelant le <xref:System.Windows.Navigation.NavigationService.Navigate%2A> méthode de la <xref:System.Windows.Navigation.NavigationService> objet. Cela requiert l’obtention d’une référence à un <xref:System.Windows.Navigation.NavigationService>.  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>Obtention d’une référence à NavigationService  
 Pour des raisons qui sont traités dans le [hôtes de Navigation](#Navigation_Hosts) section, un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application peut avoir plusieurs <xref:System.Windows.Navigation.NavigationService>. Cela signifie que votre code a besoin d’un moyen pour rechercher un <xref:System.Windows.Navigation.NavigationService>, qui est généralement le <xref:System.Windows.Navigation.NavigationService> qui a navigué vers actuel <xref:System.Windows.Controls.Page>. Vous pouvez obtenir une référence à un <xref:System.Windows.Navigation.NavigationService> en appelant le `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> (méthode). Pour obtenir le <xref:System.Windows.Navigation.NavigationService> qui a navigué vers un particulier <xref:System.Windows.Controls.Page>, vous passez une référence à la <xref:System.Windows.Controls.Page> comme argument de la <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> (méthode). Le code suivant montre comment obtenir le <xref:System.Windows.Navigation.NavigationService> pour actuel <xref:System.Windows.Controls.Page>.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 Comme raccourci pour trouver le <xref:System.Windows.Navigation.NavigationService> pour un <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implémente le <xref:System.Windows.Controls.Page.NavigationService%2A> propriété. L'exemple suivant le démontre.  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Page> peuvent obtenir uniquement une référence à son <xref:System.Windows.Navigation.NavigationService> lorsque <xref:System.Windows.Controls.Page> déclenche le <xref:System.Windows.FrameworkElement.Loaded> événement.  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>Navigation par programmation vers un objet Page  
 L’exemple suivant montre comment utiliser le <xref:System.Windows.Navigation.NavigationService> pour accéder par programme à un <xref:System.Windows.Controls.Page>. Navigation par programmation est requise car le <xref:System.Windows.Controls.Page> c'est-à-dire cible ne peut être instancié à l’aide d’un constructeur unique, non définis par défaut. Le <xref:System.Windows.Controls.Page> avec le constructeur par défaut est indiqué dans le balisage suivant et le code.  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 Le <xref:System.Windows.Controls.Page> qui accède à la <xref:System.Windows.Controls.Page> avec le constructeur par défaut est indiqué dans le balisage suivant et le code.  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 Lorsque le <xref:System.Windows.Documents.Hyperlink> sur ce <xref:System.Windows.Controls.Page> est activé, la navigation est initialisée en instanciant le <xref:System.Windows.Controls.Page> pour accéder à l’aide du constructeur par défaut et en appelant le <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> (méthode). <xref:System.Windows.Navigation.NavigationService.Navigate%2A>accepte une référence à l’objet qui le <xref:System.Windows.Navigation.NavigationService> permet d’accéder à, au lieu d’un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>Navigation par programmation avec un URI à en-tête pack  
 Si vous avez besoin construire un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] par programmation (lorsque vous ne pouvez déterminer le pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] au moment de l’exécution, par exemple), vous pouvez utiliser la <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> (méthode). L'exemple suivant le démontre.  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>Actualisation de la page active  
 A <xref:System.Windows.Controls.Page> n’est pas téléchargée si elle a le même [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que le Pack de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui est stocké dans le <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> propriété. Pour forcer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour télécharger de nouveau la page en cours, vous pouvez appeler la <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> méthode, comme indiqué dans l’exemple suivant.  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>Durée de vie de la navigation  
 Comme vous l’avez vu, il existe de nombreuses façons de démarrer la navigation. Lors de la navigation est initialisée, et pendant que la navigation est en cours d’exécution, vous pouvez suivre et influencer la navigation à l’aide des événements suivants qui sont implémentées par <xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>. Se produit quand une nouvelle navigation est demandée. Permet d’annuler la navigation.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>. Se produit périodiquement au cours d'un téléchargement, pour donner des informations sur la progression de la navigation.  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>. Se produit quand la page a été localisée et téléchargée.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>. Se produit lorsque la navigation est arrêtée (en appelant <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), ou lorsqu’une nouvelle navigation est demandée pendant une navigation est en cours d’exécution.  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>. Se produit en cas d’erreur pendant la navigation vers le contenu demandé.  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>. Se produit quand le contenu cible de la navigation est chargé et analysé, et que son rendu a commencé.  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>. Se produit au début de la navigation vers un fragment de contenu, c’est-à-dire :  
  
    -   immédiatement, si le fragment désiré est dans le contenu actuel ;  
  
    -   après le chargement du contenu source, si le fragment désiré est dans un autre contenu.  
  
 Les événements de navigation sont générés dans l’ordre indiqué sur la figure suivante.  
  
 ![Organigramme de la navigation entre les pages](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure11.png "NavigationOverviewFigure11")  
  
 En règle générale, un <xref:System.Windows.Controls.Page> n’est pas concerné sur ces événements. Il est plus probable qu’une application est concernée par les et, pour cette raison, ces événements sont également déclenchés par la <xref:System.Windows.Application> classe :  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 Chaque fois que <xref:System.Windows.Navigation.NavigationService> déclenche un événement, la <xref:System.Windows.Application> classe déclenche l’événement correspondant. <xref:System.Windows.Controls.Frame>et <xref:System.Windows.Navigation.NavigationWindow> offrent les mêmes événements pour détecter la navigation dans leurs portées respectives.  
  
 Dans certains cas, un <xref:System.Windows.Controls.Page> peut être intéressé par ces événements. Par exemple, un <xref:System.Windows.Controls.Page> peut gérer le <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> événement afin de déterminer ou non annuler la navigation en s’éloignant de lui-même. L'exemple suivant le démontre.  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 Si vous enregistrez un gestionnaire avec un événement de navigation d’un <xref:System.Windows.Controls.Page>, comme dans l’exemple précédent, vous devez également annuler l’inscription du Gestionnaire d’événements. Si vous ne le faites pas, il peut y avoir des effets secondaires en ce qui concerne la [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se souvient de navigation <xref:System.Windows.Controls.Page> navigation à l’aide de la feuille.  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>Mémorisation de la navigation avec le journal  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise deux piles pour mémoriser les pages à partir desquelles vous avez navigué : une pile Back et une pile Forward. Lorsque vous accédez à partir du <xref:System.Windows.Controls.Page> vers un nouveau <xref:System.Windows.Controls.Page> ou vers l’avant à une <xref:System.Windows.Controls.Page>, actuel <xref:System.Windows.Controls.Page> est ajouté à la *pile back*. Lorsque vous accédez à partir du <xref:System.Windows.Controls.Page> à la précédente <xref:System.Windows.Controls.Page>, actuel <xref:System.Windows.Controls.Page> est ajouté à la *pile forward*. La pile Back, la pile Forward et les fonctionnalités qui permettent de les gérer représentent le journal. Chaque élément dans la pile back et forward est une instance de la <xref:System.Windows.Navigation.JournalEntry> de classe et est appelé un *écriture*.  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Navigation dans le journal à partir d’Internet Explorer  
 Point de vue conceptuel, le journal fonctionne de la même façon que les **précédent** et **par progression** les boutons [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] faire. Ces boutons sont représentés dans la figure suivante.  
  
 ![Boutons Précédent et Suivant](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure4.png "NavigationOverviewFigure4")  
  
 Pour [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] qui sont hébergées par [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] intègre le journal dans le volet de navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Cela permet aux utilisateurs de parcourir des pages dans un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] à l’aide de la **précédent**, **par progression**, et **Pages récentes** les boutons [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]. Le journal n’est pas intégré dans [!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)] de la même façon qu’il s’agit pour [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] ou Internet Explorer 8. Au lieu de cela, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] restitue une navigation de substitution [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!IMPORTANT]
>  Dans [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], lorsqu’un utilisateur s’éloigne d’et vers un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], les entrées de journal pour les pages qui n’ont pas été conservées actifs sont conservées dans le journal. Pour savoir comment garder des pages actif, consultez [durée de vie de Page et le Journal](#PageLifetime) plus loin dans cette rubrique.  
  
 Par défaut, le texte pour chaque <xref:System.Windows.Controls.Page> qui s’affiche dans le **Pages récentes** liste des [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] est la [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour le <xref:System.Windows.Controls.Page>. Dans de nombreux cas, cela n’est pas particulièrement explicite pour l’utilisateur. Heureusement, vous pouvez changer le texte à l’aide d’une des options suivantes :  
  
1.  Le fichier joint `JournalEntry.Name` valeur d’attribut.  
  
2.  Le `Page.Title` valeur d’attribut.  
  
3.  Le `Page.WindowTitle` valeur d’attribut et la [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour actuel <xref:System.Windows.Controls.Page>.  
  
4.  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour la <xref:System.Windows.Controls.Page> actuelle. (Default)  
  
 L’ordre dans lequel les options sont listées correspond à l’ordre de priorité de recherche du texte. Par exemple, si `JournalEntry.Name` est défini, les autres valeurs sont ignorées.  
  
 L’exemple suivant utilise le `Page.Title` attribut pour modifier le texte qui s’affiche pour une entrée de journal.  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>Navigation dans le journal à l’aide de WPF  
 Bien qu’un utilisateur peut naviguer dans le journal à l’aide de la **précédent**, **par progression**, et **Pages récentes** dans [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], vous pouvez également accéder au journal à l’aide mécanismes déclaratifs et de programmation fournis par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. L’une des raisons pour ce faire consiste à fournir une navigation personnalisée [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] dans vos pages.  
  
 Vous pouvez ajouter de façon déclarative prise en charge de navigation de journal en utilisant les commandes de navigation exposées par <xref:System.Windows.Input.NavigationCommands>. L’exemple suivant montre comment utiliser la `BrowseBack` des commandes de navigation.  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 Vous pouvez naviguer par programmation le journal à l’aide d’un des membres suivants de la <xref:System.Windows.Navigation.NavigationService> classe :  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 Le journal peut également être manipulé par programme, comme indiqué dans [état du contenu retenue avec l’historique de Navigation](#RetainingContentStateWithNavigationHistory) plus loin dans cette rubrique.  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>Durée de vie d’une page et le journal  
 Considérez un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] avec plusieurs pages qui contiennent le contenu riche, y compris les graphiques, des animations et des médias. L’encombrement mémoire de pages comme celles-ci peut être assez important, en particulier si des médias audio et vidéo sont utilisés. Étant donné que les pages qui ont été navigué, par exemple le journal « souvient » un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] peut rapidement consommer une grande quantité de mémoire.  
  
 Pour cette raison, le comportement par défaut de la feuille consiste à stocker <xref:System.Windows.Controls.Page> métadonnées dans chaque entrée de journal plutôt qu’une référence à un <xref:System.Windows.Controls.Page> objet. Lorsqu’une entrée de journal est accédée, son <xref:System.Windows.Controls.Page> métadonnées sont utilisées pour créer une nouvelle instance de l’objet <xref:System.Windows.Controls.Page>. Par conséquent, chaque <xref:System.Windows.Controls.Page> cible de la navigation a la durée de vie est illustrée dans la figure suivante.  
  
 ![Durée de vie de la page](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure10.PNG "NavigationOverviewFigure10")  
  
 Bien que le comportement de journalisation par défaut permet d’enregistrer la consommation de mémoire, les performances de rendu par page peuvent être réduit ; réinstanciation un <xref:System.Windows.Controls.Page> peut consommer beaucoup de temps, en particulier si un grand nombre de contenu. Si vous avez besoin de conserver un <xref:System.Windows.Controls.Page> instance dans le journal, vous pouvez dessiner sur deux techniques pour ce faire. Tout d’abord, vous pouvez accéder par programme à un <xref:System.Windows.Controls.Page> objet en appelant le <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> (méthode).  
  
 Ensuite, vous pouvez spécifier que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] conserve une instance d’un <xref:System.Windows.Controls.Page> dans le journal en définissant le <xref:System.Windows.Controls.Page.KeepAlive%2A> propriété `true` (la valeur par défaut est `false`). Comme indiqué dans l’exemple suivant, vous pouvez définir <xref:System.Windows.Controls.Page.KeepAlive%2A> façon déclarative dans le balisage.  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 La durée de vie d’un <xref:System.Windows.Controls.Page> qui est gardée active est légèrement différent de celui n’est pas. La première fois un <xref:System.Windows.Controls.Page> qui est conservée actif cible, il est instancié comme un <xref:System.Windows.Controls.Page> qui n’est pas gardée active. Toutefois, car une instance de la <xref:System.Windows.Controls.Page> est conservée dans le journal, il n’est jamais instancié à nouveau pour tant qu’il reste dans le journal. Par conséquent, si un <xref:System.Windows.Controls.Page> possède une logique d’initialisation qui doit être appelée chaque fois que le <xref:System.Windows.Controls.Page> est accédé, vous devez la déplacer à partir du constructeur dans un gestionnaire pour le <xref:System.Windows.FrameworkElement.Loaded> événement. Comme indiqué dans l’illustration suivante, le <xref:System.Windows.FrameworkElement.Loaded> et <xref:System.Windows.FrameworkElement.Unloaded> sont toujours déclenchés chaque fois qu’un <xref:System.Windows.Controls.Page> navigué vers et à partir, respectivement.  
  
 ![Quand les événements Loaded et Unloaded sont déclenchés](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure17.png "NavigationOverviewFigure17")  
  
 Lorsqu’un <xref:System.Windows.Controls.Page> est ne pas gardée active, vous ne devez pas effectuer une des opérations suivantes :  
  
-   stocker une référence le concernant, même partiellement ;  
  
-   inscrire des gestionnaires d’événements auprès d’événements qu’il n’implémente pas.  
  
 Suivre une de ces crée des références qui force le <xref:System.Windows.Controls.Page> doit être conservé en mémoire, même après qu’il a été supprimé de la feuille.  
  
 En général, préférez la valeur par défaut <xref:System.Windows.Controls.Page> comportement de ne pas garder un <xref:System.Windows.Controls.Page> actif. Toutefois, cela a des conséquences sur l’état, comme le décrit la section suivante.  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>Conservation de l’état du contenu avec l’historique de navigation  
 Si un <xref:System.Windows.Controls.Page> n’est pas gardée active, et elle offre des contrôles qui collectent des données à partir de l’utilisateur, que se passe-t-il pour les données si un utilisateur s’éloigne d’et vers le <xref:System.Windows.Controls.Page>? Du point de vue de l’expérience utilisateur, l’utilisateur s’attend à voir les données qu’il a entrées. Malheureusement, car une nouvelle instance de la <xref:System.Windows.Controls.Page> est créée à chaque navigation, les contrôles que les données collectées sont réinstanciées et les données sont perdues.  
  
 Heureusement, le journal prend en charge la mémorisation des données entre <xref:System.Windows.Controls.Page> navigations, y compris les données de contrôle. Plus précisément, l’entrée de journal pour chaque <xref:System.Windows.Controls.Page> agit comme un conteneur temporaire associé au <xref:System.Windows.Controls.Page> état. Les étapes suivantes décrivent comment cette prise en charge est utilisé lorsqu’un <xref:System.Windows.Controls.Page> est accédé à partir de :  
  
1.  Une entrée pour actuel <xref:System.Windows.Controls.Page> est ajoutée au journal.  
  
2.  L’état de la <xref:System.Windows.Controls.Page> est stocké avec l’entrée de journal pour cette page, ce qui est ajoutée à la pile back.  
  
3.  La nouvelle <xref:System.Windows.Controls.Page> cible.  
  
 Lorsque la page <xref:System.Windows.Controls.Page> est devient la cible, à l’aide de la feuille, les étapes suivantes ont lieu :  
  
1.  Le <xref:System.Windows.Controls.Page> (l’entrée de journal du dessus sur la pile back) est instanciée.  
  
2.  Le <xref:System.Windows.Controls.Page> est actualisée avec l’état qui était stocké avec l’entrée de journal pour le <xref:System.Windows.Controls.Page>.  
  
3.  Le <xref:System.Windows.Controls.Page> devient la cible.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]utilise automatiquement cette prise en charge lorsque les contrôles suivants sont utilisés sur un <xref:System.Windows.Controls.Page>:  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ProgressBar>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Slider>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
 Si un <xref:System.Windows.Controls.Page> utilise ces contrôles, les données entrées dans les sont mémorisées sur <xref:System.Windows.Controls.Page> navigations, comme illustré dans le **couleur Favorite** <xref:System.Windows.Controls.ListBox> dans la figure suivante.  
  
 ![Page avec contrôles mémorisant l’état](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure13.png "NavigationOverviewFigure13")  
  
 Lorsqu’un <xref:System.Windows.Controls.Page> a des contrôles autres que ceux de la liste précédente, ou lorsque l’état est stocké dans des objets personnalisés, vous devez écrire du code pour que le journal se souvienne de l’état entre <xref:System.Windows.Controls.Page> navigations.  
  
 Si vous devez n’oubliez pas de petites parties d’état entre <xref:System.Windows.Controls.Page> navigations, vous pouvez utiliser les propriétés de dépendance (consultez <xref:System.Windows.DependencyProperty>) qui sont configurés avec le <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> indicateur de métadonnées.  
  
 Si l’état que votre <xref:System.Windows.Controls.Page> a besoin de se rappeler lors des navigations comprend plusieurs éléments de données, il peut s’avérer moins de code pour encapsuler votre état dans une seule classe et implémenter la <xref:System.Windows.Navigation.IProvideCustomContentState> interface.  
  
 Si vous devez naviguer à travers différents États d’un seul <xref:System.Windows.Controls.Page>, sans naviguer à partir de la <xref:System.Windows.Controls.Page> lui-même, vous pouvez utiliser <xref:System.Windows.Navigation.IProvideCustomContentState> et <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>Cookies  
 Une autre façon que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications peuvent stocker des données est cookies, qui sont créées, mises à jour et supprimés à l’aide de la <xref:System.Windows.Application.SetCookie%2A> et <xref:System.Windows.Application.GetCookie%2A> méthodes. Les cookies que vous pouvez créer dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont les mêmes cookies utilisent de que d’autres types d’applications Web ; les cookies sont des éléments de données qui sont stockées par une application sur un ordinateur client pendant ou à travers les sessions d’application arbitraires. Les données de cookie prennent généralement la forme d’une paire nom/valeur au format suivant.  
  
 *Nom* `=` *Valeur*  
  
 Lorsque les données sont transmises à <xref:System.Windows.Application.SetCookie%2A>, avec le <xref:System.Uri> de l’emplacement pour lequel le cookie doit être défini, un cookie est créé en mémoire, et il est disponible uniquement pour la durée de la session d’application actuel. Ce type de cookie est appelé un *cookie de session*.  
  
 Pour stocker un cookie dans des sessions d’application, vous devez lui ajouter une date d’expiration au format suivant.  
  
 *NOM* `=` *VALEUR* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 Un cookie avec une date d’expiration est stocké dans le courant [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] dossier des fichiers Internet temporaires de l’installation jusqu'à ce que le cookie expire. Un cookie est appelé un *cookie persistant* parce qu’il persiste entre les sessions d’application.  
  
 Récupération de session et les cookies persistants en appelant le <xref:System.Windows.Application.GetCookie%2A> méthode, en passant le <xref:System.Uri> de l’emplacement où le cookie a été défini avec la <xref:System.Windows.Application.SetCookie%2A> (méthode).  
  
 Voici quelques-unes des façons dont les cookies sont pris en charge dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]applications autonomes et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] peut créer et gérer les cookies.  
  
-   Les cookies qui sont créés par un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est accessible à partir du navigateur.  
  
-   Les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] du même domaine peuvent créer et partager des cookies.  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]et [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] pages du même domaine peuvent créer et partager des cookies.  
  
-   Les cookies sont distribués lorsque [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] et libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages effectuer des requêtes Web.  
  
-   Les deux de niveau supérieur [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] hébergé dans IFRAMES peuvent accéder aux cookies.  
  
-   Prise en charge de cookie dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est identique pour tous les navigateurs pris en charge.  
  
-   Dans [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)], stratégie P3P qui concerne les cookies est honorée par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], notamment en ce qui concerne le premier tiers et tiers [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>Navigation structurée  
 Si vous avez besoin passer des données à partir d’un <xref:System.Windows.Controls.Page> vers un autre, vous pouvez passer les données en tant qu’arguments à un constructeur par défaut de la <xref:System.Windows.Controls.Page>. Notez que si vous utilisez cette technique, vous devez garder le <xref:System.Windows.Controls.Page> alive ; si non, la prochaine fois que vous accédez à la <xref:System.Windows.Controls.Page>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] réinstancie la <xref:System.Windows.Controls.Page> à l’aide du constructeur par défaut.  
  
 Vous pouvez également votre <xref:System.Windows.Controls.Page> peuvent implémenter des propriétés qui sont définies avec les données qui doivent être transmises. Cela se complique, toutefois, lorsqu’un <xref:System.Windows.Controls.Page> a besoin pour passer des données vers le <xref:System.Windows.Controls.Page> qui a navigué vers elle. Le problème est que navigation ne prend en charge des mécanismes pour garantir qu’un <xref:System.Windows.Controls.Page> s’affichera à après qu’il est accédé à partir de. Pour l’essentiel, la navigation ne prend pas en charge la sémantique d’appel/de retour. Pour résoudre ce problème, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit le <xref:System.Windows.Navigation.PageFunction%601> classe que vous pouvez utiliser pour s’assurer qu’un <xref:System.Windows.Controls.Page> est renvoyé dans un prévisible et structurée de manière. Pour plus d’informations, consultez [Structured Navigation Overview](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>NavigationWindow, classe  
 À ce stade, vous avez découvert la gamme des services de navigation que vous êtes le plus susceptible d’utiliser pour générer des applications au contenu navigable. Ces services sont présentés dans le contexte de [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], bien qu’ils ne sont pas limités à [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Systèmes d’exploitation modernes et [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] applications tirer parti de l’expérience de navigateur, les utilisateurs modernes pour incorporer une navigation de style navigateur dans des applications autonomes. Voici quelques exemples usuels :  
  
-   **Dictionnaire des synonymes** : pour naviguer parmi des choix de mots.  
  
-   **Explorateur de fichiers** : pour naviguer parmi des fichiers et des dossiers.  
  
-   **Assistants** : pour décomposer une tâche complexe en plusieurs pages parmi lesquelles il est possible de naviguer. Un exemple est l’Assistant Composants Windows qui gère l’ajout et suppression de [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] fonctionnalités.  
  
 Pour incorporer la navigation de style navigateur dans vos applications autonomes, vous pouvez utiliser la <xref:System.Windows.Navigation.NavigationWindow> classe. <xref:System.Windows.Navigation.NavigationWindow>dérive de <xref:System.Windows.Window> et étend la même prise en charge pour la navigation qui [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] fournir. Vous pouvez utiliser <xref:System.Windows.Navigation.NavigationWindow> comme fenêtre principale de votre application autonome ou comme une fenêtre secondaire comme une boîte de dialogue.  
  
 Pour implémenter un <xref:System.Windows.Navigation.NavigationWindow>, comme avec la plupart des classes de niveau supérieur dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, et ainsi de suite), vous utilisez une combinaison de balisage et code-behind. L'exemple suivant le démontre.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 Ce code crée un <xref:System.Windows.Navigation.NavigationWindow> qui accède automatiquement à un <xref:System.Windows.Controls.Page> (HomePage.xaml) lorsque le <xref:System.Windows.Navigation.NavigationWindow> est ouvert. Si le <xref:System.Windows.Navigation.NavigationWindow> est la fenêtre principale de l’application, vous pouvez utiliser la `StartupUri` attribut pour le lancer. Ce cas de figure est illustré dans le balisage suivant.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 L’illustration suivante montre le <xref:System.Windows.Navigation.NavigationWindow> en tant que la fenêtre principale d’une application autonome.  
  
 ![Fenêtre principale](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure18.png "NavigationOverviewFigure18")  
  
 Dans l’illustration, vous pouvez voir que la <xref:System.Windows.Navigation.NavigationWindow> possède un titre, bien qu’il n’a pas été défini le <xref:System.Windows.Navigation.NavigationWindow> code d’implémentation de l’exemple précédent. Au lieu de cela, le titre est défini à l’aide de la <xref:System.Windows.Controls.Page.WindowTitle%2A> propriété, qui est indiquée dans le code suivant.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 Définition de la <xref:System.Windows.Controls.Page.WindowWidth%2A> et <xref:System.Windows.Controls.Page.WindowHeight%2A> propriétés affecte également la <xref:System.Windows.Navigation.NavigationWindow>.  
  
 En règle générale, vous implémentez votre propre <xref:System.Windows.Navigation.NavigationWindow> lorsque vous devez personnaliser son comportement ou son apparence. Si vous ne faites ni l’un, ni l’autre, vous pouvez utiliser un raccourci. Si vous spécifiez le Pack de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] d’un <xref:System.Windows.Controls.Page> en tant que le <xref:System.Windows.Application.StartupUri%2A> dans une application autonome, <xref:System.Windows.Application> crée automatiquement un <xref:System.Windows.Navigation.NavigationWindow> pour héberger le <xref:System.Windows.Controls.Page>. Le balisage suivant montre comment y parvenir.  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 Si vous souhaitez une fenêtre d’application secondaire comme une boîte de dialogue pour être un <xref:System.Windows.Navigation.NavigationWindow>, vous pouvez utiliser le code dans l’exemple suivant pour l’ouvrir.  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 L’illustration suivante affiche le résultat.  
  
 ![Boîte de dialogue](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure19.png "NavigationOverviewFigure19")  
  
 Comme vous pouvez le voir, <xref:System.Windows.Navigation.NavigationWindow> affiche [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]-style **précédent** et **par progression** boutons qui permettent aux utilisateurs de naviguer dans le journal. Ces boutons fournissent la même expérience utilisateur, comme le montre la figure suivante.  
  
 ![Boutons Précédent et Suivant dans NavigationWindow](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure20.png "NavigationOverviewFigure20")  
  
 Si vos pages fournissent leur propre interface utilisateur et le prise en charge de navigation de journal, vous pouvez masquer la **précédent** et **par progression** boutons affichés par <xref:System.Windows.Navigation.NavigationWindow> en définissant la valeur de la <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> propriété `false`.  
  
 Vous pouvez également utiliser la prise en charge de la personnalisation dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pour remplacer le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de la <xref:System.Windows.Navigation.NavigationWindow> lui-même.  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Frame, classe  
 Les deux le navigateur et <xref:System.Windows.Navigation.NavigationWindow> sont des fenêtres qui hébergent du contenu navigable. Dans certains cas, les applications ont un contenu qui n’a pas besoin d’être hébergé par une fenêtre entière. À la place, ce contenu est hébergé dans un autre contenu. Vous pouvez insérer du contenu navigable dans tout autre contenu à l’aide de la <xref:System.Windows.Controls.Frame> classe. <xref:System.Windows.Controls.Frame>Fournit la même prise en charge en tant que <xref:System.Windows.Navigation.NavigationWindow> et [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
 L’exemple suivant montre comment ajouter un <xref:System.Windows.Controls.Frame> à un <xref:System.Windows.Controls.Page> façon déclarative à l’aide de la `Frame` élément.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 Cette balise définit le `Source` attribut de la `Frame` élément avec un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pour le <xref:System.Windows.Controls.Page> qui le <xref:System.Windows.Controls.Frame> doit naviguer initialement. L’illustration suivante montre un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] avec un <xref:System.Windows.Controls.Page> qui a un <xref:System.Windows.Controls.Frame> qui a navigué entre plusieurs pages.  
  
 ![Frame ayant navigué entre plusieurs pages](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure5.png "NavigationOverviewFigure5")  
  
 Vous ne devez uniquement utiliser <xref:System.Windows.Controls.Frame> à l’intérieur du contenu d’un <xref:System.Windows.Controls.Page>. Il est également courant d’héberger un <xref:System.Windows.Controls.Frame> à l’intérieur du contenu d’un <xref:System.Windows.Window>.  
  
 Par défaut, <xref:System.Windows.Controls.Frame> utilise uniquement son propre journal en l’absence d’un autre journal. Si un <xref:System.Windows.Controls.Frame> fait partie du contenu qui est hébergé dans un <xref:System.Windows.Navigation.NavigationWindow> ou [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> utilise le journal qui appartienne à la <xref:System.Windows.Navigation.NavigationWindow> ou [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Parfois, cependant, un <xref:System.Windows.Controls.Frame> devra peut-être être responsable de son propre journal. L’une des raisons pour ce faire consiste à permettre la navigation de journal dans les pages qui sont hébergées par un <xref:System.Windows.Controls.Frame>. Cela est illustré par la figure suivante.  
  
 ![Diagramme de frame et de page](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure7.png "NavigationOverviewFigure7")  
  
 Dans ce cas, vous pouvez configurer le <xref:System.Windows.Controls.Frame> à utiliser son propre journal en définissant le <xref:System.Windows.Controls.Frame.JournalOwnership%2A> propriété de la <xref:System.Windows.Controls.Frame> à <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>. Ce cas de figure est illustré dans le balisage suivant.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 L’exemple suivant illustre l’effet de la navigation dans un <xref:System.Windows.Controls.Frame> qui utilise son propre journal.  
  
 ![Frame utilisant son propre journal](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure8.png "NavigationOverviewFigure8")  
  
 Notez que les entrées de journal sont affichées par le volet de navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans les <xref:System.Windows.Controls.Frame>, plutôt que par [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)].  
  
> [!NOTE]
>  Si un <xref:System.Windows.Controls.Frame> fait partie du contenu qui est hébergé dans un <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> utilise son propre journal et, par conséquent, affiche sa propre navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Si votre expérience utilisateur requiert un <xref:System.Windows.Controls.Frame> pour fournir son propre journal sans afficher le volet de navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], vous pouvez masquer le volet de navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] en définissant le <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> à <xref:System.Windows.Visibility.Hidden>. Ce cas de figure est illustré dans le balisage suivant.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>Hôtes de navigation  
 <xref:System.Windows.Controls.Frame>et <xref:System.Windows.Navigation.NavigationWindow> sont des classes qui sont appelés hôtes de navigation. A *hôte de navigation* est une classe qui peut naviguer vers et afficher le contenu. Pour ce faire, chaque hôte de navigation utilise son propre <xref:System.Windows.Navigation.NavigationService> et du journal. La construction de base d’un hôte de navigation est illustrée dans la figure suivante.  
  
 ![Diagrammes du navigateur](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure15.png "NavigationOverviewFigure15")  
  
 Fondamentalement, cela permet <xref:System.Windows.Navigation.NavigationWindow> et <xref:System.Windows.Controls.Frame> pour fournir la même navigation prise en charge qu’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] fournit lorsqu’il est hébergé dans le navigateur.  
  
 Outre l’utilisation de <xref:System.Windows.Navigation.NavigationService> et d’un journal, les hôtes de navigation implémentent les mêmes membres que <xref:System.Windows.Navigation.NavigationService> implémente. Cela est illustré par la figure suivante.  
  
 ![Journal dans un frame et un NavigationWindow](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure24.png "NaivgationOverviewFigure24")  
  
 Cela vous permet de programmer la prise en charge de la navigation directement par rapport à eux. Vous pouvez envisager cela si vous avez besoin fournir une navigation personnalisée [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour un <xref:System.Windows.Controls.Frame> qui est hébergé dans un <xref:System.Windows.Window>. En outre, les deux types implémentent des membres supplémentaires, liées à la navigation, y compris `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) et `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), vous permettent d’énumérer les entrées de journal à l’arrière pile et le transfert de la pile, respectivement.  
  
 Comme cela a déjà été mentionné, plusieurs journaux peuvent exister dans une application. L’exemple suivant illustre ce cas de figure.  
  
 ![Plusieurs journaux dans une application](../../../../docs/framework/wpf/app-development/media/naivgationoverviewfigure25.png "NaivgationOverviewFigure25")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>Navigation vers un autre contenu que des pages XAML  
 Dans cette rubrique, <xref:System.Windows.Controls.Page> et pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ont été utilisées pour illustrer les différentes fonctionnalités de navigation de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Toutefois, un <xref:System.Windows.Controls.Page> qui est compilé dans une application n’est pas le seul type de contenu qui peut être parcouru à et pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ne sont pas la seule façon pour identifier le contenu.  
  
 Comme indiqué dans cette section, vous pouvez également accéder à faible [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichiers [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] fichiers et des objets.  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Navigation vers des fichiers XAML libre  
 Libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est un fichier avec les caractéristiques suivantes :  
  
-   Ne contient que [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (autrement dit, aucun code).  
  
-   Il a une déclaration d’espace de noms appropriée.  
  
-   Son nom de fichier porte l’extension .xaml.  
  
 Par exemple, considérez le contenu suivant qui est stocké comme un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier Person.xaml.  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 Quand vous double-cliquez sur le fichier, le navigateur s’ouvre et navigue vers le contenu, qu’il affiche. Ce cas est illustré dans la figure suivante.  
  
 ![Affichage du contenu du fichier Person.XAML](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure21.png "NavigationOverviewFigure21")  
  
 Vous pouvez afficher un texte libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier dans la liste suivante :  
  
-   site web sur la machine locale, un intranet ou Internet ;  
  
-   A [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] partage de fichiers.  
  
-   disque local.  
  
 Libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier peut être ajouté aux Favoris du navigateur, ou être la page d’accueil du navigateur.  
  
> [!NOTE]
>  Pour plus d’informations sur la publication et le lancement libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages, consultez [déploiement d’une Application WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
 Une limitation relative au libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est que vous pouvez uniquement héberger le contenu qui est sécurisé pour s’exécuter avec une confiance partielle. Par exemple, `Window` ne peut pas être l’élément racine d’un faible [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>Navigation vers des fichiers HTML à l’aide d’un Frame  
 Comme prévu, vous pouvez également accéder à [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. Vous devez simplement fournir un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui utilise le schéma http. Par exemple, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] montre un <xref:System.Windows.Controls.Frame> qui accède à un [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] page.  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 Navigation vers [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] requiert des autorisations spéciales. Par exemple, vous ne pouvez pas accéder à partir d’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui s’exécute dans le sandbox de sécurité de confiance partielle de zone Internet. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>Navigation vers des fichiers HTML à l’aide du contrôle WebBrowser  
 Le <xref:System.Windows.Controls.WebBrowser> contrôle prend en charge [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] hébergement de document, navigation et de script/code de l’interopérabilité. Pour plus d’informations concernant la <xref:System.Windows.Controls.WebBrowser> du contrôle, consultez <xref:System.Windows.Controls.WebBrowser>.  
  
 Comme <xref:System.Windows.Controls.Frame>, la navigation vers [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] à l’aide de <xref:System.Windows.Controls.WebBrowser> requiert des autorisations spéciales. Par exemple, à partir d’une application de confiance partielle, vous pouvez naviguer uniquement à [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] situé sur le site d’origine. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>Navigation vers des objets personnalisés  
 Si vous avez des données qui sont stockées en tant qu’objets personnalisés, permet d’afficher les données consiste à créer un <xref:System.Windows.Controls.Page> avec du contenu qui est lié à ces objets (consultez [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)). En revanche, si vous n’avez pas besoin de la charge de traitement supplémentaire liée à la création d’une page entière juste pour afficher les objets, vous pouvez naviguer directement vers ces derniers.  
  
 Prendre en compte la `Person` classe est implémentée dans le code suivant.  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 Pour naviguer vers elle, vous appelez le <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> méthode, comme illustré dans le code suivant.  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 L’illustration suivante affiche le résultat.  
  
 ![Page de navigation vers une classe](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure22.png "NavigationOverviewFigure22")  
  
 Dans cette illustration, vous pouvez voir que rien d’utile n’est affiché. En fait, la valeur affichée est la valeur de retour de la `ToString` méthode pour le **personne** objet ; par défaut, c’est la seule valeur [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] peut utiliser pour représenter votre objet. Vous pouvez substituer le `ToString` méthode pour retourner des informations plus explicites, bien qu’il est toujours être uniquement une valeur de chaîne. Vous pouvez utiliser une technique qui tire parti des fonctionnalités de présentation [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consiste à utiliser un modèle de données. Vous pouvez implémenter un modèle de données qui [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pouvez associer à un objet d’un type particulier. Le code suivant montre un modèle de données pour le `Person` objet.  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 Ici, le modèle de données est associé le `Person` type à l’aide de la `x:Type` extension de balisage dans le `DataType` attribut. Le modèle de données lie ensuite `TextBlock` éléments (consultez <xref:System.Windows.Controls.TextBlock>) aux propriétés de la `Person` classe. L’illustration suivante montre l’apparence de mise à jour de la `Person` objet.  
  
 ![Navigation vers une classe comportant un modèle de données](../../../../docs/framework/wpf/app-development/media/navigationoverviewfigure23.png "NavigationOverviewFigure23")  
  
 Cette technique présente un avantage, elle vous permet d’afficher vos objets de manière cohérente dans la totalité de votre application grâce à la réutilisation du modèle de données.  
  
 Pour plus d’informations sur les modèles de données, consultez [vue d’ensemble de la création de modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="Security"></a>   
## <a name="security"></a>Sécurité  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]prise en charge de la navigation permet [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] être cible de la navigation sur Internet et il permet aux applications d’héberger le contenu tiers. Pour protéger les applications et les utilisateurs du comportement dangereux, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit un éventail de fonctionnalités de sécurité qui sont abordées dans [sécurité](../../../../docs/framework/wpf/security-wpf.md) et [sécurité de confiance partielle WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Application.SetCookie%2A>  
 <xref:System.Windows.Application.GetCookie%2A>  
 [Vue d’ensemble de la gestion d’applications](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [URI à en-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Vue d’ensemble de la navigation structurée](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)  
 [Vue d’ensemble des topologies de navigation](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/app-development/navigation-how-to-topics.md)  
 [Déploiement d’une application WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
