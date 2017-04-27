---
title: "Vue d&#39;ensemble des compl&#233;ments WPF | Microsoft Docs"
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
  - "modèle de complément du .NET Framework (WPF)"
  - "compléments (WPF), architecture"
  - "compléments (WPF), avantages"
  - "compléments (WPF), limitations"
  - "compléments (WPF), performances"
  - "compléments (WPF), interface utilisateur"
  - "compléments et interface utilisateur (WPF)"
  - "compléments et applications de navigateur XAML (WPF)"
  - "vue d'ensemble des compléments (WPF)"
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
caps.latest.revision: 36
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 35
---
# Vue d&#39;ensemble des compl&#233;ments WPF
<a name="Introduction"></a> Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] inclut un modèle de complément que les développeurs peuvent utiliser pour créer des applications prenant en charge l'extensibilité des compléments.  Ce modèle de complément permet la création de compléments qui s'intègrent aux fonctionnalités des applications et les étendent.  Dans certains scénarios, les applications doivent également afficher les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fournies par les compléments.  Cette rubrique montre comment [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] optimise le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour prendre en charge ces scénarios, l'architecture sur laquelle ils s'appuient, ses avantages et ses limitations.  
  
   
  
<a name="Requirements"></a>   
## Composants requis  
 Il convient de connaître le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  Pour plus d'informations, consultez [Compléments et extensibilité](../../../../ml/index.xml).  
  
<a name="AddInsOverview"></a>   
## Vue d'ensemble des compléments  
 Pour éviter la complexité qu'impliquent le redéploiement et la recompilation d'applications en vue d'incorporer les nouvelles fonctionnalités, les applications mettent en œuvre des mécanismes d'extensibilité qui permettent aux développeurs \(tant internes que tiers\) de créer d'autres applications qui s'y intègrent.  La méthode la plus courante de prise en charge de ce type d'extensibilité consiste à utiliser des compléments \(également appelés « modules complémentaires », « add\-ins » et « plug\-ins »\).  Voici quelques exemples d'applications réelles qui exposent l'extensibilité avec des compléments :  
  
-   Modules complémentaires d'Internet Explorer  
  
-   Plug\-ins Windows Media Player.  
  
-   Compléments Visual Studio.  
  
 Par exemple, le modèle de complément Windows Media Player permet aux développeurs tiers d'implémenter des « plug\-ins » qui étendent cette application de différentes façons, notamment en créant des décodeurs et des encodeurs des formats multimédias qui ne sont pas pris en charge en mode natif par Windows Media Player \(par exemple, DVD, MP3\), des effets audio et des apparences.  Chaque modèle de complément est construit pour exposer les fonctionnalités uniques d'une application, bien que plusieurs entités et comportements soient communs à tous les modèles de compléments.  
  
 Les trois principales entités de solutions d'extensibilité des compléments classiques sont les *contrats*, les *compléments* et les *applications hôtes*.  Les contrats définissent la manière dont les compléments s'intègrent aux applications hôtes de deux manières :  
  
-   Les compléments s'intègrent aux fonctionnalités implémentées par les applications hôtes.  
  
-   Les applications hôtes exposent les fonctionnalités des compléments auxquels elles s'intègrent.  
  
 Pour pouvoir utiliser des compléments, les applications hôtes doivent les rechercher et les charger au moment de l'exécution.  Par conséquent, les applications qui prennent en charge des compléments ont les responsabilités supplémentaires suivantes :  
  
-   **Découverte** : recherche de compléments adhérant aux contrats pris en charge par les applications hôte.  
  
-   **Activation** : chargement, exécution et établissement de la communication avec les compléments.  
  
-   **Isolation** : utilisation de domaines ou de processus d'application pour établir des limites d'isolation protégeant les applications des problèmes potentiels de sécurité et d'exécution avec les compléments.  
  
-   **Communication** : autorisation pour les compléments et les applications d'hôte à communiquer entre eux au travers des limites d'isolation par des méthodes d'appel et le passage de données.  
  
-   **Gestion de la durée de vie** : chargement et déchargement des domaines et des processus d'application de façon propre et prédictible \(consultez [Domaines d'application](../../../../docs/framework/app-domains/application-domains.md)\).  
  
-   **Suivi des versions** : garantie que les applications hôte et les compléments peuvent encore communiquer lorsque de nouvelles versions de l'un ou l'autre sont créées.  
  
 Enfin, le développement d'un modèle de complément fiable est une tâche non triviale.  Pour cette raison, le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournit une infrastructure pour la génération de modèles de compléments.  
  
> [!NOTE]
>  Pour des informations détaillées sur les compléments, consultez [Compléments et extensibilité](../../../../ml/index.xml).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## Vue d'ensemble du modèle de complément .NET Framework  
 Le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], qui se trouve dans l'espace de noms <xref:System.AddIn>, contient un jeu de types conçus pour simplifier le développement d'une extensibilité des compléments.  L'unité fondamentale du modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] est le *contrat*, qui définit la manière dont une application hôte et un complément communiquent l'un avec l'autre.  Un contrat est exposé à une application hôte à l'aide d'une *vue* spécifique de l'application hôte du contrat.  De même, une *vue* spécifique au complément du contrat est exposée au complément.  Un *adaptateur* est utilisé pour permettre à une application hôte et un complément de communiquer entre leurs vues respectives du contrat.  Les contrats, les vues et les adaptateurs sont appelés "segments" et un jeu de segments connexes constitue un *pipeline*.  Les pipelines sont la fondation sur laquelle le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] prend en charge la découverte, l'activation, l'isolation de sécurité et l'isolation d'exécution \(qui utilise aussi bien les domaines d'application que les processus\), la communication, le management de la durée de vie et le suivi des versions.  
  
 Toutes ces prises en charge permettent aux développeurs de générer des compléments qui s'intègrent aux fonctionnalités d'une application hôte.  Toutefois, certains scénarios requièrent que les applications hôtes affichent les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fournies par les compléments.  Du fait que chaque technologie de présentation dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] a son propre modèle pour implémenter les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ne prend en charge aucune technologie de présentation particulière.  Au lieu de cela, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] avec la prise en charge de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour les compléments.  
  
<a name="WPFAddInModel"></a>   
## Compléments WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], utilisé conjointement avec le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], vous permet de prendre en charge divers scénarios nécessitant que les applications hôtes affichent les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] à partir de compléments.  Plus particulièrement, ces scénarios sont pris en charge par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] avec les deux modèles de programmation suivants :  
  
1.  **Le complément retourne une interface utilisateur**.  Un complément retourne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à l'application hôte par le biais d'un appel de méthode, comme défini par le contrat.  Ce scénario est utilisé dans les cas suivants :  
  
    -   L'apparence d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] retournée par un complément dépend des données ou des conditions existant uniquement au moment de l'exécution, par exemple les rapports générés dynamiquement.  
  
    -   L'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des services fournis par un complément diffère de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des applications hôtes qui peuvent utiliser le complément.  
  
    -   Le complément exécute principalement un service pour l'application hôte et signale l'état à cette dernière avec une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **Le complément est une interface utilisateur**.  Un complément est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], comme défini par le contrat.  Ce scénario est utilisé dans les cas suivants :  
  
    -   Un complément ne fournit pas de services autres que le fait d'être affiché, par exemple une publicité.  
  
    -   L'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des services fournis par un complément est commune à toutes les applications hôtes qui peuvent utiliser ce complément, comme une calculatrice ou un sélecteur de couleurs.  
  
 Ces scénarios requièrent que les objets de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] puissent être transmis entre les domaines des applications hôtes et des applications complémentaires.  Étant donné que le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] repose sur la communication à distance pour communiquer entre des domaines d'applications, les objets échangés entre ces derniers doivent être accessibles à distance.  
  
 Un objet accessible à distance est une instance d'une classe qui effectue une ou plusieurs des opérations suivantes :  
  
-   Dérive de la classe <xref:System.MarshalByRefObject>.  
  
-   Implémente l'interface <xref:System.Runtime.Serialization.ISerializable>.  
  
-   L'attribut <xref:System.SerializableAttribute> lui est appliqué.  
  
> [!NOTE]
>  Pour plus d'informations sur la création d'objets [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] accessibles à distance, consultez [Making Objects Remotable](http://msdn.microsoft.com/fr-fr/01197253-3f13-43b7-894d-9683e431192a).  
  
 Les types d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ne sont pas accessibles à distance.  Pour résoudre ce problème, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour permettre l'affichage de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] créée par des compléments à partir d'applications hôtes.  Cette prise en charge est fournie par deux types de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] : l'interface <xref:System.AddIn.Contract.INativeHandleContract> et deux méthodes statiques implémentées par la classe <xref:System.AddIn.Pipeline.FrameworkElementAdapters> : <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  À un niveau élevé, ces types et méthodes sont utilisés de la manière suivante :  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] requiert que les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fournies par les compléments soient des classes directement ou indirectement dérivées de <xref:System.Windows.FrameworkElement>, par exemple des formes, des contrôles, des contrôles utilisateur, des panneaux de disposition et des pages.  
  
2.  Chaque fois que le contrat déclare qu'une interface utilisateur sera transmise entre le complément et l'application hôte, elle doit être déclarée comme un <xref:System.AddIn.Contract.INativeHandleContract> \(et non un <xref:System.Windows.FrameworkElement>\) ; <xref:System.AddIn.Contract.INativeHandleContract> est une représentation accessible à distance de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément qui peut être transmise à travers les limites d'isolation.  
  
3.  Avant d'être transmis à partir du domaine d'application du complément, un <xref:System.Windows.FrameworkElement> est conditionné comme un <xref:System.AddIn.Contract.INativeHandleContract> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Après avoir été transmis au domaine d'application de l'application hôte, le <xref:System.AddIn.Contract.INativeHandleContract> doit être reconditionné comme un <xref:System.Windows.FrameworkElement> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 L'utilisation de <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> dépend du scénario spécifique.  Les sections suivantes décrivent chaque modèle de programmation.  
  
<a name="ReturnUIFromAddInContract"></a>   
## Le complément retourne une interface utilisateur  
 Pour qu'un complément retourne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à une application hôte, les conditions suivantes sont nécessaires :  
  
1.  L'application hôte, le complément et le pipeline doivent être créés, comme décrit dans la documentation de [Compléments et extensibilité](../../../../ml/index.xml) de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
2.  Le contrat doit implémenter <xref:System.AddIn.Contract.IContract> et, pour retourner une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], il doit déclarer une méthode avec une valeur de retour de type <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  L'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] transmise entre le complément et l'application hôte doit dériver directement ou indirectement de <xref:System.Windows.FrameworkElement>.  
  
4.  L'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] retournée par le complément doit être convertie d'un <xref:System.Windows.FrameworkElement> en un <xref:System.AddIn.Contract.INativeHandleContract> avant de passer par la limite d'isolation.  
  
5.  L'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] retournée doit être convertie d'un <xref:System.AddIn.Contract.INativeHandleContract> en un <xref:System.Windows.FrameworkElement> après être passée par la limite d'isolation.  
  
6.  L'application hôte affiche le <xref:System.Windows.FrameworkElement> retourné.  
  
 Pour obtenir un exemple expliquant comment implémenter un complément qui retourne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Créer un complément qui retourne une interface utilisateur](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## Le complément est une interface utilisateur  
 Lorsqu'un complément est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], les conditions suivantes sont nécessaires :  
  
1.  L'application hôte, le complément et le pipeline doivent être créés, comme décrit dans la documentation de [Compléments et extensibilité](../../../../ml/index.xml) de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
2.  L'interface du contrat pour le complément doit implémenter <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Le complément transmis à l'application hôte doit dériver directement ou indirectement de <xref:System.Windows.FrameworkElement>.  
  
4.  Le complément doit être converti d'un <xref:System.Windows.FrameworkElement> en un <xref:System.AddIn.Contract.INativeHandleContract> avant de passer par la limite d'isolation.  
  
5.  Le complément doit être converti d'un <xref:System.AddIn.Contract.INativeHandleContract> en un <xref:System.Windows.FrameworkElement> après être passé par la limite d'isolation.  
  
6.  L'application hôte affiche le <xref:System.Windows.FrameworkElement> retourné.  
  
 Pour obtenir un exemple expliquant comment implémenter un complément d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Créer un complément qui est une interface utilisateur](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## Retour de plusieurs interfaces utilisateur à partir d'un complément  
 Les compléments proposent souvent plusieurs [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] affichables par les applications hôtes.  Par exemple, supposons un complément qui est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fournissant aussi des informations d'état à l'application hôte, également sous la forme d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  Un complément de ce type peut être implémenté à l'aide d'une combinaison de techniques provenant des modèles [Le complément retourne une interface utilisateur](#ReturnUIFromAddInContract) et [Le complément est une interface utilisateur](#AddInIsAUI).  
  
<a name="AddInsAndXBAPs"></a>   
## Compléments et applications du navigateur XAML  
 Dans les exemples présentés jusque\-là, l'application hôte a été installée comme une application autonome.  Toutefois, les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] peuvent également héberger des compléments, bien que ceux\-ci s'accompagnent des conditions de création et d'implémentation supplémentaires suivantes :  
  
-   Le manifeste de l'application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit être configuré spécialement pour télécharger le pipeline \(dossiers et assemblys\) et l'assembly de complément dans le cache de l'application [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] sur l'ordinateur client, dans le même dossier que [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   Le code de [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] permettant de découvrir et de charger des compléments doit utiliser le cache de l'application [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] pour [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] comme l'emplacement du complément et du pipeline.  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit charger le complément dans un contexte de sécurité spécial si le complément fait référence à des fichiers à part qui se trouvent au site d'origine ; en cas d'hébergement par [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], les compléments ne peuvent faire référence qu'à des fichiers à part qui se trouvent au site d'origine de l'application hôte.  
  
 Ces tâches sont décrites en détail dans les sous\-sections suivantes.  
  
### Configuration du pipeline et du complément pour un déploiement ClickOnce  
 Les [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sont téléchargés et exécutés dans un dossier sûr du cache de déploiement [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)].  Pour qu'une application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] héberge un complément, le pipeline et l'assembly du complément doivent également être téléchargés dans ce dossier sûr.  Pour cela, vous devez configurer le manifeste de l'application de sorte qu'il comprenne le pipeline et l'assembly du complément à télécharger.  Cette opération peut être effectuée le plus facilement dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], bien que le pipeline et l'assembly du complément doivent se trouver dans le dossier racine du projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] de l'hôte pour que [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] puisse détecter les assemblys de pipeline.  
  
 Par conséquent, la première étape consiste à générer le pipeline et l'assembly du complément à la racine du projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] en définissant la sortie de génération de chaque projet d'assembly de pipeline et d'assembly de complément.  Le tableau suivant indique les chemins de sortie de génération des projets d'assembly de pipeline et de complément se trouvant dans le même dossier de solution et racine que le projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] de l'hôte.  
  
 Tableau 1 : Chemins de sortie de la génération des assemblys de pipeline hébergés par un XBAP  
  
|Projet d'assembly de pipeline|Chemin de sortie de la génération|  
|-----------------------------------|---------------------------------------|  
|Contrat|`..  \HostXBAP\Contracts\`|  
|Vue de complément|`..  \HostXBAP\AddInViews\`|  
|Adaptateur côté complément|`..  \HostXBAP\AddInSideAdapters\`|  
|Adaptateur côté hôte|`..  \HostXBAP\HostSideAdapters\`|  
|Complément|`..  \HostXBAP\AddIns\WPFAddIn1`|  
  
 L'étape suivante consiste à spécifier les assemblys de pipeline et l'assembly de complément comme fichiers de contenu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] en effectuant les opérations suivantes :  
  
1.  Inclusion de l'assembly de pipeline et de complément dans le projet en cliquant avec le bouton droit sur chaque dossier de pipeline dans l'Explorateur de solutions et en choisissant **Inclure dans le projet**.  
  
2.  Affectation de la valeur **Contenu** à l'option **Action de génération** de chaque assembly de pipeline et de complément dans la fenêtre **Propriétés**.  
  
 La dernière étape consiste à configurer le manifeste de l'application de manière à inclure les fichiers d'assembly de pipeline et de complément à télécharger.  Les fichiers doivent se trouver dans les dossiers à la racine du dossier du cache [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] que l'application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] occupe.  La configuration peut être réalisée dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] en effectuant les opérations suivantes :  
  
1.  Cliquez avec le bouton droit sur le projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], puis cliquez sur **Propriétés**, **Publier** et enfin **Fichiers d'application**.  
  
2.  Dans la boîte de dialogue **Fichiers d'application**, attribuez aux options **État de la publication** et **Groupe de téléchargement** de chaque pipeline et DLL de complément les valeurs **Inclure \(Automatique\)** et **\(Requis\)**, respectivement.  
  
### Utilisation du pipeline et du complément à partir de la base de l'application  
 Lorsque le pipeline et le complément sont configurés pour le déploiement de [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], ils sont téléchargés dans le même dossier de cache [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] que [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  Pour utiliser le pipeline et le complément à partir de [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], le code de [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit les obtenir à partir de la base de l'application.  Les différents types et membres du modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] permettant d'utiliser des pipelines et des compléments fournissent une prise en charge spéciale de ce scénario.  Dans un premier temps, le chemin est identifié par la valeur d'énumération <xref:System.AddIn.Hosting.PipelineStoreLocation>.  Vous utilisez cette valeur avec les surcharges des membres du complément adéquats permettant d'utiliser des pipelines incluant les éléments suivants :  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
-   [AddInStore.FindAddIns\(Type, PipelineStoreLocation, String\<xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=fullName>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
### Accès au site d'origine de l'hôte  
 Pour veiller à ce qu'un complément puisse référencer des fichiers à partir du site d'origine, le complément doit être chargé avec l'isolation de sécurité équivalente à l'application hôte.  Ce niveau de sécurité est identifié par la valeur d'énumération <xref:System.AddIn.Hosting.AddInSecurityLevel?displayProperty=fullName>, et est transmis à la méthode <xref:System.AddIn.Hosting.AddInToken.Activate%2A> lorsqu'un complément est activé.  
  
<a name="WPFAddInModelArchitecture"></a>   
## Architecture des compléments WPF  
 Au niveau le plus élevé, comme nous l'avons observé, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet aux compléments [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] d'implémenter des [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] \(directement ou indirectement dérivées de <xref:System.Windows.FrameworkElement>\) à l'aide de <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  Il en résulte qu'un <xref:System.Windows.FrameworkElement> est retourné à l'application hôte, affiché à partir de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans l'application hôte.  
  
 Dans les scénarios de compléments d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] simples, ces détails sont tout ce dont un développeur a besoin.  Dans des scénarios plus complexes, en particulier ceux qui essaient d'utiliser des services [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supplémentaires tels qu'une disposition, des ressources et la liaison de données, il convient d'avoir une connaissance plus approfondie de la manière dont [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] en intégrant la prise en charge de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] afin de comprendre ses avantages et ses limitations.  
  
 Fondamentalement, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ne transmet pas d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément à une application hôte ; au lieu de cela, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] transmet le handle de fenêtre Win32 de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] en utilisant l'interopérabilité [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Ainsi, lorsqu'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est transmise d'un complément à une application hôte, les événements suivants se produisent :  
  
-   Du côté complément, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] acquiert un handle de fenêtre pour l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui sera affichée par l'application hôte.  Le handle de fenêtre est encapsulé par une classe [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] interne dérivée de <xref:System.Windows.Interop.HwndSource> et implémente <xref:System.AddIn.Contract.INativeHandleContract>.  Une instance de cette classe est retournée par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et est marshalée du domaine d'application du complément au domaine d'application de l'application hôte.  
  
-   Du côté application hôte, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] reconditionne le <xref:System.Windows.Interop.HwndSource> comme une classe [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] interne dérivée de <xref:System.Windows.Interop.HwndHost> et consomme <xref:System.AddIn.Contract.INativeHandleContract>.  Une instance de cette classe est retournée par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> à l'application hôte.  
  
 <xref:System.Windows.Interop.HwndHost> existe pour afficher les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], identifiées par les handles de fenêtre, à partir des [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Pour plus d'informations, consultez [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 En résumé, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existent pour permettre de transmettre le handle de fenêtre d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] d'un complément à une application hôte, où il est encapsulé par un <xref:System.Windows.Interop.HwndHost> et où l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de l'application hôte est affichée.  
  
> [!NOTE]
>  Du fait qu'elle obtienne un <xref:System.Windows.Interop.HwndHost>, l'application hôte ne peut pas convertir l'objet retourné par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> en le type en lequel elle est implémentée par le complément \(par exemple, un <xref:System.Windows.Controls.UserControl>\).  
  
 De par sa nature, <xref:System.Windows.Interop.HwndHost> a certaines limitations qui affectent la manière dont les applications hôtes peuvent l'utiliser.  Toutefois, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend <xref:System.Windows.Interop.HwndHost> avec plusieurs fonctionnalités pour les scénarios complémentaires.  Ces avantages et limitations sont décrits ci\-dessous.  
  
<a name="WPFAddInModelBenefits"></a>   
## Avantages des compléments WPF  
 Étant donné que les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] des compléments [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont affichées à partir des applications hôtes à l'aide d'une classe interne dérivée de <xref:System.Windows.Interop.HwndHost>, ces [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] sont contraintes par les capacités de <xref:System.Windows.Interop.HwndHost> en ce qui concerne les services de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], comme les dispositions, les rendus, la liaison de données, les styles, les modèles et les ressources.  Toutefois, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend sa sous\-classe <xref:System.Windows.Interop.HwndHost> interne avec des fonctionnalités supplémentaires, notamment :  
  
-   Tabulation entre l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'une application hôte et l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément.  Notez que le modèle de programmation "Le complément est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" requiert que l'adaptateur côté complément remplace <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> pour permettre la tabulation, que le complément présente un niveau de confiance suffisant ou partiel.  
  
-   Respect des spécifications d'accessibilité des [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de compléments affichées à partir des [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] des applications hôtes.  
  
-   Permettre aux applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] de s'exécuter sans risque dans plusieurs scénarios de domaines d'application.  
  
-   Empêcher l'accès illégal aux handles de fenêtre de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des compléments lorsque ces derniers s'exécutent avec l'isolation de sécurité \(autrement dit, un sandbox de sécurité présentant un niveau de confiance partiel\).  L'appel de <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> garantit cette sécurité :  
  
    -   Pour le modèle de programmation "Le complément retourne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]", le seul moyen de transmettre le handle de fenêtre de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément au\-delà de la limite d'isolation consiste à appeler <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   Pour le modèle de programmation "Le complément est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]", il convient de remplacer <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> sur l'adaptateur côté complément et d'appeler <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> \(comme indiqué dans les exemples précédents\), de même qu'il faut appeler l'implémentation `QueryContract` de l'adaptateur côté complément à partir de l'adaptateur côté hôte.  
  
-   Fournir une protection contre l'exécution de plusieurs domaines d'application.  Du fait des limitations qu'impliquent les domaines d'application, les exceptions non gérées qui sont renvoyées dans les domaines d'application complémentaires entraînent l'arrêt complet de l'application, y compris en présence d'une limite d'isolation.  Toutefois, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] et le modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] offrent une solution simple à ce problème et améliorent la stabilité des applications.  Un complément [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] qui affiche une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] crée un <xref:System.Windows.Threading.Dispatcher> pour le thread sur lequel s'exécute le domaine d'application, si l'application hôte est une application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Vous pouvez détecter toutes les exceptions non gérées qui se produisent dans le domaine d'application en gérant l'événement <xref:System.Windows.Threading.Dispatcher.UnhandledException> du <xref:System.Windows.Threading.Dispatcher> du complément [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Vous pouvez obtenir le <xref:System.Windows.Threading.Dispatcher> à partir de la propriété <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>.  
  
<a name="WPFAddInModelLimitations"></a>   
## Limitations des compléments WPF  
 Au\-delà des avantages que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ajoute aux comportements par défaut fournis par <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> et les handles de fenêtre, les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de compléments affichées à partir d'applications hôtes impliquent également des limitations :  
  
-   Les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de compléments affichées à partir d'une application hôte ne respectent pas le comportement de découpage de cette dernière.  
  
-   Le concept d'*espace de rendu* dans les scénarios d'interopérabilité s'applique également aux compléments \(consultez [Vue d'ensemble des régions de technologie](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)\).  
  
-   Les services de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'une application hôte, tels que l'héritage de ressources, la liaison de données les commandes, ne sont pas automatiquement disponibles pour l'[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] du complément.  Pour fournir ces services au complément, vous devez mettre à jour le pipeline.  
  
-   L'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément ne peut pas être pivotée, mise à l'échelle, inclinée ou transformée de quelque autre manière \(consultez [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)\).  
  
-   Le contenu des [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de compléments qui est restitué par des opérations de dessin à partir de l'espace de noms <xref:System.Drawing> peut inclure une fusion alpha.  Toutefois, l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément ainsi que l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de l'application hôte qui comprennent ce contenu doivent être opaques à 100 % ; en d'autres termes, la propriété `Opacity` doit avoir la valeur 1 dans les deux interfaces.  
  
-   Si la propriété <xref:System.Windows.Window.AllowsTransparency%2A> d'une fenêtre de l'application hôte qui contient une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de complément a la valeur `true`, le complément est alors invisible.  Cette remarque s'applique même si l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément est opaque à 100 % \(autrement dit, la propriété `Opacity` a la valeur 1\).  
  
-   L'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément doit apparaître au\-dessus d'autres éléments [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dans la même fenêtre de niveau supérieur.  
  
-   Aucune partie de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément ne peut être restituée à l'aide d'un <xref:System.Windows.Media.VisualBrush>.  Au lieu de cela, le complément peut prendre une capture instantanée de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] générée afin de créer une bitmap qui peut être transmise à l'application hôte à l'aide de méthodes définies par le contrat.  
  
-   Les fichiers multimédia ne peuvent pas être lus à partir d'un <xref:System.Windows.Controls.MediaElement> dans l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément.  
  
-   Les événements de souris générés pour l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément ne sont ni reçus ni déclenchés par l'application hôte, et la propriété `IsMouseOver` de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de l'application hôte a la valeur `false`.  
  
-   Lorsque le focus se déplace entre des contrôles dans l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément, les événements `GotFocus` et `LostFocus` ne sont ni reçu ni déclenchés par l'application hôte.  
  
-   La partie d'une application hôte qui contient l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément apparaît en blanc à l'impression.  
  
-   Tous les répartiteurs \(consultez <xref:System.Windows.Threading.Dispatcher>\) créés par l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément doivent être arrêtés manuellement avant que le complément propriétaire ne soit déchargé si l'exécution de l'application hôte se poursuit.  Le contrat peut implémenter des méthodes qui permettent à l'application hôte de signaler le complément avant son déchargement, permettant ainsi à l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément d'arrêter ses répartiteurs.  
  
-   Si l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d'un complément est un <xref:System.Windows.Controls.InkCanvas> ou contient un <xref:System.Windows.Controls.InkCanvas>, il n'est pas possible de décharger le complément.  
  
<a name="PerformanceOptimization"></a>   
## Optimisation des performances  
 Par défaut, lorsque plusieurs domaines d'application sont utilisés, les différents assemblys [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] requis par chaque application sont tous chargés dans le domaine des applications en question.  En conséquence, le temps nécessaire à la création de domaines d'application et au démarrage des applications dans ces domaines peut affecter la performance.  Toutefois, le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] offre un moyen de réduire le temps de démarrage en indiquant aux applications de partager des assemblys dans différents domaines d'application si ceux\-ci sont déjà chargés.  Pour ce faire, vous utilisez l'attribut <xref:System.LoaderOptimizationAttribute>, qui doit être appliqué à la méthode de point d'entrée \(`Main`\).  Dans ce cas, vous devez utiliser uniquement le code pour implémenter votre définition d'application \(consultez [Vue d'ensemble de la gestion d'applications](../../../../docs/framework/wpf/app-development/application-management-overview.md)\).  
  
## Voir aussi  
 <xref:System.LoaderOptimizationAttribute>   
 [Compléments et extensibilité](../../../../ml/index.xml)   
 [Domaines d'application](../../../../docs/framework/app-domains/application-domains.md)   
 [.NET Framework Remoting Overview](http://msdn.microsoft.com/fr-fr/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)   
 [Making Objects Remotable](http://msdn.microsoft.com/fr-fr/01197253-3f13-43b7-894d-9683e431192a)   
 [Rubriques Comment](../../../../docs/framework/wpf/app-development/how-to-topics.md)