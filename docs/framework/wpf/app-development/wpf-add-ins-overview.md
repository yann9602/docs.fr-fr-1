---
title: "Vue d'ensemble des compléments WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffd45957b41cdfd8488aedd865aa70ef5b2634b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="wpf-add-ins-overview"></a>Vue d'ensemble des compléments WPF
<a name="Introduction"></a> Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] inclut un modèle de complément que les développeurs peuvent utiliser pour créer des applications prenant en charge l’extensibilité des compléments. Ce modèle de complément permet de créer des compléments qui s’intègrent aux applications et étendent leurs fonctionnalités. Dans certains scénarios, les applications doivent également afficher les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fournies par les compléments. Cette rubrique montre comment [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] optimise le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour prendre en charge ces scénarios, l’architecture sur laquelle il repose, ainsi que ses avantages et ses limitations.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Prérequis  
 Une bonne connaissance du modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] est nécessaire. Pour plus d’informations, consultez [Compléments et extensibilité](../../../../docs/framework/add-ins/index.md).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Vue d’ensemble des compléments  
 Pour éviter la complexité des tâches de redéploiement et de recompilation des applications durant l’incorporation de nouvelles fonctionnalités, les applications offrent des mécanismes d’extensibilité qui permettent aux développeurs (aussi bien internes que tiers) de créer d’autres applications qui s’y intègrent. La méthode la plus répandue pour prendre en charge ce type d’extensibilité consiste à utiliser des compléments (également appelés « modules complémentaires », « extensions » et « plug-ins »). Voici quelques exemples d’applications réelles qui offrent une extensibilité à l’aide de compléments :  
  
-   modules complémentaires d’Internet Explorer ;  
  
-   plug-ins du Lecteur Windows Media ;  
  
-   compléments Visual Studio.  
  
 Par exemple, le modèle de complément du Lecteur Windows Media permet aux développeurs tiers d’implémenter des « plug-ins » pour étendre le Lecteur Windows Media de différentes façons, notamment en créant des décodeurs et encodeurs de formats multimédias non pris en charge en mode natif par le Lecteur Windows Media (DVD, MP3, par exemple), des effets audio et des apparences. Chaque modèle de complément est conçu pour exposer les fonctionnalités uniques d’une application, bien que plusieurs entités et comportements soient communs à tous les modèles de compléments.  
  
 Les trois principales entités de solutions d’extensibilité des compléments classiques sont les *contrats*, les *compléments* et les *applications hôtes*. Les contrats définissent la manière dont les compléments s’intègrent aux applications hôtes de deux manières :  
  
-   Les compléments s’intègrent aux fonctionnalités implémentées par les applications hôtes.  
  
-   Les applications hôtes exposent les fonctionnalités auxquelles les compléments peuvent s’intégrer.  
  
 Pour permettre l’utilisation des compléments, les applications hôtes doivent les rechercher et les charger au moment de l’exécution. Ainsi, les applications qui prennent en charge des compléments ont les responsabilités supplémentaires suivantes :  
  
-   **Découverte** : recherche des compléments adhérant aux contrats pris en charge par les applications hôtes.  
  
-   **Activation** : chargement, exécution et établissement de la communication avec les compléments.  
  
-   **Isolation** : utilisation de domaines ou de processus d’application pour établir des limites d’isolation protégeant les applications des problèmes potentiels de sécurité et d’exécution liés aux compléments.  
  
-   **Communication** : autorisation pour les compléments et les applications hôtes de communiquer au travers des limites d’isolation via l’appel de méthodes et le passage de données.  
  
-   **Gestion de la durée de vie** : chargement et déchargement des domaines et processus d’application de façon propre et prévisible (consultez [Domaines d’application](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Gestion de versions** : vérification de la communication entre les nouvelles versions des applications hôtes et des compléments.  
  
 Enfin, le développement d’un modèle de complément robuste est une tâche non négligeable. C’est la raison pour laquelle le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournit une infrastructure de génération de modèles de compléments.  
  
> [!NOTE]
>  Pour plus d’informations sur les compléments, consultez [Compléments et extensibilité](../../../../docs/framework/add-ins/index.md).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>Vue d’ensemble du modèle de complément du .NET Framework  
 Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] -modèle de complément, trouvé dans le <xref:System.AddIn> espace de noms contient un ensemble de types qui sont conçus pour simplifier le développement d’extensibilité du complément. L’unité fondamentale du modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] est le *contrat*, qui définit la façon dont une application hôte et un complément communiquent entre eux. Un contrat est exposé à une application hôte à l’aide d’une *vue* spécifique à l’application hôte du contrat. De même, une *vue* spécifique au complément du contrat est exposée au complément. Un *adaptateur* permet à une application hôte et à un complément de communiquer entre les vues respectives du contrat. Les contrats, les vues et les adaptateurs sont appelés des segments. Un ensemble de segments connexes constitue un *pipeline*. Le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] s’appuie sur les pipelines pour prendre en charge la découverte, l’activation, l’isolation de sécurité et l’isolation d’exécution (à l’aide des domaines et des processus d’application), la communication, la gestion de la durée de vie et la gestion de versions.  
  
 L’ensemble de cette prise en charge permet aux développeurs de générer des compléments qui s’intègrent aux fonctionnalités d’une application hôte. Toutefois, dans certains scénarios, les applications hôtes doivent afficher les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fournies par les compléments. Comme chaque technologie de présentation du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] a son propre modèle d’implémentation des [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ne prend en charge aucune technologie de présentation particulière. Au lieu de cela, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] avec la prise en charge de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des compléments.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>Compléments WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], utilisé conjointement avec le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], vous permet de prendre en charge divers scénarios où les applications hôtes doivent afficher les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] des compléments. Plus précisément, ces scénarios sont pris en charge par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] via les deux modèles de programmation suivants :  
  
1.  **Le complément retourne une IU (interface utilisateur)**. Un complément retourne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à l’application hôte via un appel de méthode, comme le définit le contrat. Ce scénario est utilisé dans les cas suivants :  
  
    -   L’apparence d’une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] retournée par un complément dépend des données ou des conditions qui existent uniquement au moment de l’exécution, par exemple pour les rapports générés dynamiquement.  
  
    -   L’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des services fournis par un complément diffère de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des applications hôtes qui peuvent utiliser le complément.  
  
    -   Le complément exécute principalement un service pour l’application hôte et signale l’état à cette dernière avec une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **Le complément est une interface utilisateur**. Un complément est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], comme le définit le contrat. Ce scénario est utilisé dans les cas suivants :  
  
    -   Un complément ne fournit pas d’autres services que celui d’être affiché, par exemple une publicité.  
  
    -   L’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des services fournis par un complément est commune à toutes les applications hôtes qui peuvent utiliser ce complément, par exemple une calculatrice ou un sélecteur de couleurs.  
  
 Ces scénarios doivent permettre le passage des objets de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] entre le domaine d’application hôte et le domaine d’application du complément. Comme le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] repose sur la communication à distance pour la communication entre les domaines d’application, les objets passés entre ces derniers doivent être accessibles à distance.  
  
 Un objet accessible à distance est une instance d’une classe qui effectue une ou plusieurs des opérations suivantes :  
  
-   Dérive de la <xref:System.MarshalByRefObject> classe.  
  
-   Implémente l'interface <xref:System.Runtime.Serialization.ISerializable>.  
  
-   A la <xref:System.SerializableAttribute> attribut appliqué.  
  
> [!NOTE]
>  Pour plus d’informations sur la création d’objets du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] accessibles à distance, consultez [Rendre des objets accessibles à distance](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a).  
  
 Les types d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ne sont pas accessibles à distance. Pour résoudre ce problème, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] afin de permettre l’affichage de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] créée par les compléments à partir des applications hôtes. Cette prise en charge est fournie par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] par deux types : les <xref:System.AddIn.Contract.INativeHandleContract> interface et les deux méthodes statiques implémentées par le <xref:System.AddIn.Pipeline.FrameworkElementAdapters> classe : <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. À un niveau élevé, ces types et méthodes sont utilisés de la manière suivante :  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]requiert que [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fournies par les compléments sont des classes qui dérivent directement ou indirectement de <xref:System.Windows.FrameworkElement>, tels que des formes, des contrôles, des contrôles utilisateur, des panneaux de disposition et des pages.  
  
2.  Chaque fois que le contrat déclare qu’une interface utilisateur sera transmise entre le complément et l’application hôte, elle doit être déclarée comme une <xref:System.AddIn.Contract.INativeHandleContract> (pas un <xref:System.Windows.FrameworkElement>) ; <xref:System.AddIn.Contract.INativeHandleContract> est une représentation accessible à distance de la macro complémentaire [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui peuvent être passés entre les limites d’isolation.  
  
3.  Avant d’être passé à partir de domaine d’application de la macro complémentaire, un <xref:System.Windows.FrameworkElement> est empaqueté comme un <xref:System.AddIn.Contract.INativeHandleContract> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Après avoir été transmis au domaine d’application de l’application hôte, le <xref:System.AddIn.Contract.INativeHandleContract> doivent être reconstitués comme un <xref:System.Windows.FrameworkElement> en appelant <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Comment <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> servent dépend du scénario spécifique. Les sections suivantes fournissent des détails sur chaque modèle de programmation.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>Le complément retourne une interface utilisateur  
 Pour permettre à un complément de retourner une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à une application hôte, les conditions suivantes doivent être remplies :  
  
1.  L’application hôte, le complément et le pipeline doivent être créés, comme indiqué dans la documentation [Compléments et extensibilité](../../../../docs/framework/add-ins/index.md) du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
2.  Le contrat doit implémenter <xref:System.AddIn.Contract.IContract> et, pour retourner un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], le contrat doit déclarer une méthode avec une valeur de retour de type <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui lui est passé entre le complément et l’hôte application doit dériver directement ou indirectement de <xref:System.Windows.FrameworkElement>.  
  
4.  Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui est retourné par le complément doit être converti d’une <xref:System.Windows.FrameworkElement> à un <xref:System.AddIn.Contract.INativeHandleContract> avant de passer par la limite d’isolation.  
  
5.  Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] retourné doit être convertie d’une <xref:System.AddIn.Contract.INativeHandleContract> à un <xref:System.Windows.FrameworkElement> après être passé par la limite d’isolation.  
  
6.  L’application hôte affiche retourné <xref:System.Windows.FrameworkElement>.  
  
 Pour obtenir un exemple montrant comment implémenter un complément qui retourne une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Créer un complément qui retourne une interface utilisateur](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>Le complément est une interface utilisateur  
 Quand un complément est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], les éléments suivants sont nécessaires :  
  
1.  L’application hôte, le complément et le pipeline doivent être créés, comme indiqué dans la documentation [Compléments et extensibilité](../../../../docs/framework/add-ins/index.md) du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
2.  L’interface de contrat pour le complément doit implémenter <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  Le complément est passé à l’application hôte doit dériver directement ou indirectement à partir de <xref:System.Windows.FrameworkElement>.  
  
4.  Le complément doit être converti d’une <xref:System.Windows.FrameworkElement> à un <xref:System.AddIn.Contract.INativeHandleContract> avant de passer par la limite d’isolation.  
  
5.  Le complément doit être converti d’une <xref:System.AddIn.Contract.INativeHandleContract> à un <xref:System.Windows.FrameworkElement> après être passé par la limite d’isolation.  
  
6.  L’application hôte affiche retourné <xref:System.Windows.FrameworkElement>.  
  
 Pour obtenir un exemple montrant comment implémenter un complément qui est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consultez [Créer un complément qui est une interface utilisateur](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Retour de plusieurs interfaces utilisateur à partir d’un complément  
 Les compléments proposent souvent plusieurs [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] pouvant être affichées par les applications hôtes. Prenons l’exemple d’un complément qui est une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fournissant aussi des informations d’état à l’application hôte, également sous forme d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Un complément de ce type peut être implémenté à l’aide d’une combinaison de techniques provenant des modèles [Le complément retourne une interface utilisateur](#ReturnUIFromAddInContract) et [Le complément est une interface utilisateur](#AddInIsAUI).  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Compléments et applications de navigateur XAML  
 Dans les exemples présentés jusqu’à maintenant, l’application hôte a été installée en tant qu’application autonome. Toutefois, les applications [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] peuvent également héberger des compléments, bien que ceux-ci s’accompagnent des exigences de génération et d’implémentation supplémentaires suivantes :  
  
-   Le manifeste de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit être configuré spécialement pour télécharger le pipeline (dossiers et assemblys) et l’assembly de complément dans le cache d’application [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] sur la machine cliente, dans le même dossier que l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   Le code de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] permettant de découvrir et de charger les compléments doit utiliser le cache d’application [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] pour l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] comme emplacement de pipeline et de complément.  
  
-   L’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit charger le complément dans un contexte de sécurité spécial si ce complément référence des fichiers libres situés sur le site d’origine. Quand ils sont hébergés par l’application [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], les compléments peuvent uniquement référencer les fichiers libres situés sur le site d’origine de l’application hôte.  
  
 Ces tâches sont décrites en détail dans les sous-sections suivantes.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Configuration du pipeline et du complément pour un déploiement ClickOnce  
 Les applications [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] sont téléchargées et exécutées dans un dossier sécurisé du cache de déploiement [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]. Pour qu’une application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] héberge un complément, l’assembly de pipeline et de complément doit également être téléchargé dans ce dossier sécurisé. Ainsi, vous devez configurer le manifeste de l’application pour qu’il contienne l’assembly de pipeline et de complément à télécharger. Le plus simple est d’effectuer cette opération dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Toutefois, l’assembly de pipeline et de complément doit se trouver dans le dossier racine du projet d’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] de l’hôte pour que [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] puisse détecter les assemblys de pipeline.  
  
 La première étape consiste donc à générer l’assembly de pipeline et de complément à la racine du projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] en définissant la sortie de build de chaque projet d’assembly de pipeline et d’assembly de complément. Le tableau suivant présente les chemins de sortie de build des projets d’assembly de pipeline et du projet d’assembly de complément se trouvant dans le même dossier solution et racine que le projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] de l’hôte.  
  
 Tableau 1 : Chemins de sortie de build des assemblys de pipeline hébergés par une application XBAP  
  
|Projet d’assembly de pipeline|Chemin de sortie de la génération|  
|-------------------------------|-----------------------|  
|Contrat|`..\HostXBAP\Contracts\`|  
|Vue de complément|`..\HostXBAP\AddInViews\`|  
|Adaptateur côté complément|`..\HostXBAP\AddInSideAdapters\`|  
|Adaptateur côté hôte|`..\HostXBAP\HostSideAdapters\`|  
|Complément|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 L’étape suivante consiste à spécifier les assemblys de pipeline et l’assembly de complément en tant que fichiers de contenu [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] en effectuant les opérations ci-dessous :  
  
1.  Ajoutez l’assembly de pipeline et de complément au projet en cliquant avec le bouton droit sur chaque dossier de pipeline dans l’Explorateur de solutions, puis choisissez **Inclure dans le projet**.  
  
2.  Affectez à l’**Action de génération** de chaque assembly de pipeline et de complément le **Contenu** de la fenêtre **Propriétés**.  
  
 La dernière étape consiste à configurer le manifeste de l’application pour inclure les fichiers d’assembly de pipeline et de complément à télécharger. Les fichiers doivent se trouver dans des dossiers situés à la racine du dossier du cache [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] occupé par l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Vous pouvez procéder à la configuration dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] en effectuant les opérations suivantes :  
  
1.  Cliquez avec le bouton droit sur le projet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], cliquez sur **Propriétés**, sur **Publier**, puis sur le bouton **Fichiers d’application**.  
  
2.  Dans la boîte de dialogue **Fichiers d’application**, affectez à l’**État de la publication** de chaque DLL de pipeline et de complément la valeur **Inclure (automatique)**, puis affectez au **Groupe de téléchargement** de chaque DLL de pipeline et de complément la valeur **(Requis)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Utilisation du pipeline et du complément à partir de la base de l’application  
 Quand le pipeline et le complément sont configurés pour le déploiement [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], ils sont téléchargés dans le même dossier de cache [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] que l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Pour permettre l’utilisation du pipeline et du complément à partir de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], le code de l’application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] doit les obtenir à partir de la base de l’application. Les divers types et membres du modèle de complément [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] permettant d’utiliser des pipelines et des compléments fournissent une prise en charge spéciale de ce scénario. Tout d’abord, le chemin d’accès est identifié par le <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> valeur d’énumération. Vous utilisez cette valeur avec les surcharges des membres de complément adéquats pour utiliser des pipelines incluant les éléments suivants :  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Accès au site d’origine de l’hôte  
 Pour garantir qu’un complément puisse référencer des fichiers à partir du site d’origine, ce complément doit être chargé avec l’isolation de sécurité équivalente à l’application hôte. Ce niveau de sécurité est identifié par le <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> valeur d’énumération et transmis à la <xref:System.AddIn.Hosting.AddInToken.Activate%2A> méthode lorsqu’un complément est activé.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>Architecture des compléments WPF  
 Le niveau le plus élevé, comme nous l’avons vu, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] active [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] les compléments pour implémenter [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] (qui dérivent directement ou indirectement <xref:System.Windows.FrameworkElement>) à l’aide de <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Le résultat est que l’application hôte est retournée une <xref:System.Windows.FrameworkElement> qui s’affiche à partir de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans l’application hôte.  
  
 Dans les scénarios de compléments d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] simples, ces détails sont tout ce dont un développeur a besoin. Dans les scénarios plus complexes, en particulier ceux qui essaient d’utiliser des services [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supplémentaires tels que la disposition, les ressources et la liaison de données, il convient d’avoir une connaissance plus approfondie de la façon dont [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] en intégrant la prise en charge de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour comprendre ses avantages et ses limitations.  
  
 Fondamentalement, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ne passe pas d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] entre un complément et une application hôte. À la place, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] passe le handle de fenêtre Win32 de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à l’aide de l’interopérabilité [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ainsi, quand une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est passée d’un complément à une application hôte, les événements suivants se produisent :  
  
-   Côté complément, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] acquiert un handle de fenêtre pour l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui doit être affichée par l’application hôte. Le handle de fenêtre est encapsulé par un interne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classe qui dérive de <xref:System.Windows.Interop.HwndSource> et implémente <xref:System.AddIn.Contract.INativeHandleContract>. Une instance de cette classe est retournée par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> et est marshalé en domaine d’application du complément pour le domaine d’application de l’application hôte.  
  
-   Du côté application hôte, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Repackage le <xref:System.Windows.Interop.HwndSource> en tant que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classe qui dérive de <xref:System.Windows.Interop.HwndHost> et consomme <xref:System.AddIn.Contract.INativeHandleContract>. Une instance de cette classe est retournée par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> à l’application hôte.  
  
 <xref:System.Windows.Interop.HwndHost>existe pour afficher [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], identifiée par les handles de fenêtre, à partir de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Pour plus d’informations, consultez [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 En résumé, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, et <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existent pour autoriser le handle de fenêtre pour un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à passer à partir d’un complément à une application hôte, où il est encapsulé par un <xref:System.Windows.Interop.HwndHost> et affiche l’hôte l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  Étant donné que l’application hôte obtienne un <xref:System.Windows.Interop.HwndHost>, l’application hôte ne peut pas convertir l’objet retourné par <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> au type, elle est implémentée par le complément (par exemple, un <xref:System.Windows.Controls.UserControl>).  
  
 De par sa nature, <xref:System.Windows.Interop.HwndHost> avec certaines limitations qui affectent comment héberger des applications peuvent les utiliser. Toutefois, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] étend <xref:System.Windows.Interop.HwndHost> avec plusieurs fonctionnalités pour les scénarios de complément. Ces avantages et limitations sont décrits ci-dessous.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>Avantages des compléments WPF  
 Étant donné que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] complément [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] sont affichés à partir d’héberger des applications à l’aide d’une classe interne qui dérive de <xref:System.Windows.Interop.HwndHost>, ces [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] sont limitées par les capacités de <xref:System.Windows.Interop.HwndHost> par rapport à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] services tels que la mise en page, le rendu, la liaison de données, les styles, modèles et ressources. Toutefois, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] augmente son interne <xref:System.Windows.Interop.HwndHost> sous-classe avec des fonctionnalités supplémentaires qui incluent les éléments suivants :  
  
-   Tabulation entre l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’une application hôte et l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’un complément. Notez que le « add-in est un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]« modèle de programmation requiert l’adaptateur côté complément remplace <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> pour activer la tabulation, si le complément est totalement de confiance ou partiellement.  
  
-   Respect des exigences d’accessibilité des [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de complément affichées à partir des [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] d’application hôte.  
  
-   Exécution sans risque des applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dans plusieurs scénarios de domaine d’application.  
  
-   Blocage de tout accès non conforme aux handles de fenêtres de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des compléments quand ces derniers s’exécutent avec une isolation de sécurité (c’est-à-dire dans un bac à sable (sandbox) de sécurité partiellement fiable). Appel de <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> garantit cette sécurité :  
  
    -   Pour les « complément retourne un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]« modèle de programmation, la seule façon de passer le handle de fenêtre pour un complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] entre l’isolation Limite consiste à appeler <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   Pour le » est un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]» de programmation de modèle, substitution <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> sur l’adaptateur côté complément et l’appel <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (comme indiqué dans les exemples précédents) est requis, comme l’adaptateur côté complément appelle `QueryContract` implémentation à partir de l’adaptateur côté hôte.  
  
-   Protection de l’exécution de plusieurs domaines d’application. En raison des limitations liées aux domaines d’application, les exceptions non prises en charge qui sont levées dans les domaines d’application de complément entraînent l’arrêt brutal de l’application, même s’il existe une limite d’isolation. Toutefois, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] et le modèle de complément du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] offrent une solution simple à ce problème et améliorent la stabilité des applications. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] complément qui affiche un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] crée un <xref:System.Windows.Threading.Dispatcher> pour le thread qui le domaine d’application s’exécute, si l’application hôte est un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application. Vous pouvez détecter non prise en charge toutes les exceptions qui se produisent dans le domaine d’application en gérant la <xref:System.Windows.Threading.Dispatcher.UnhandledException> l’événement de la [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] du complément <xref:System.Windows.Threading.Dispatcher>. Vous pouvez obtenir le <xref:System.Windows.Threading.Dispatcher> à partir de la <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> propriété.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>Limitations des compléments WPF  
 Au-delà des avantages qui [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ajoute les comportements par défaut fournis par <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>et les handles de fenêtre, il existe également des limitations pour les compléments [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] qui s’affichent à partir d’applications de l’hôte :  
  
-   Les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de complément affichées à partir d’une application hôte ne respectent pas le comportement de découpage de cette dernière.  
  
-   Le concept d’*espace de rendu* des scénarios d’interopérabilité s’applique également aux compléments (consultez [Vue d’ensemble des régions de technologie](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Les services d’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’une application hôte, par exemple l’héritage de ressources, la liaison de données et l’exécution de commandes, ne sont pas automatiquement accessibles aux [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de complément. Pour fournir ces services au complément, vous devez mettre à jour le pipeline.  
  
-   L’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’un complément ne peut pas être pivotée, mise à l’échelle, inclinée ou transformée (consultez [Vue d’ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   Contenu à l’intérieur de complément [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] qui est restitué en dessinant des opérations à partir de la <xref:System.Drawing> espace de noms peut inclure une fusion alpha. Toutefois, l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément et l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de l’application hôte qui la contient doivent être opaques à 100 %. En d’autres termes, la propriété `Opacity` doit avoir la valeur 1 pour les deux interfaces utilisateur.  
  
-   Si le <xref:System.Windows.Window.AllowsTransparency%2A> propriété d’une fenêtre dans l’application hôte qui contient un complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a la valeur `true`, le complément est invisible. Cela est vrai même si l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément est opaque à 100 % (en d’autres termes, si la propriété `Opacity` a la valeur 1).  
  
-   L’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’un complément doit apparaître au-dessus des autres éléments [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dans la même fenêtre de niveau supérieur.  
  
-   Aucune partie d’un complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] peut être rendu à l’aide un <xref:System.Windows.Media.VisualBrush>. À la place, le complément peut prendre un instantané de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] générée pour créer une image bitmap pouvant être passée à l’application hôte à l’aide des méthodes définies par le contrat.  
  
-   Impossible de lire des fichiers multimédias à partir d’un <xref:System.Windows.Controls.MediaElement> dans un complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Les événements de souris générés pour l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément ne sont ni reçus, ni déclenchés par l’application hôte. De plus, la propriété `IsMouseOver` de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de l’application hôte a la valeur `false`.  
  
-   Quand le focus se déplace entre les contrôles de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’un complément, les événements `GotFocus` et `LostFocus` ne sont ni reçus, ni déclenchés par l’application hôte.  
  
-   La partie d’une application hôte qui contient l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’un complément apparaît en blanc à l’impression.  
  
-   Tous les répartiteurs (consultez <xref:System.Windows.Threading.Dispatcher>) créé par le complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] doivent être arrêtés manuellement avant que la macro complémentaire propriétaire soit déchargée si l’application hôte continue l’exécution. Le contrat peut implémenter des méthodes qui permettent à l’application hôte de signaler le complément avant son déchargement. Ainsi, l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du complément peut arrêter ses répartiteurs.  
  
-   Si un complément [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est un <xref:System.Windows.Controls.InkCanvas> ou contient un <xref:System.Windows.Controls.InkCanvas>, vous ne pouvez pas décharger le complément.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Optimisation des performances  
 Par défaut, quand plusieurs domaines d’application sont utilisés, les différents assemblys du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nécessaires à chaque application sont tous chargés dans le domaine de l’application concernée. Ainsi, le temps nécessaire à la création de domaines d’application et au démarrage des applications dans ces domaines peut affecter les performances. Toutefois, le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vous permet de réduire le temps de démarrage en indiquant aux applications de partager les assemblys entre les différents domaines d’application, si ceux-ci sont déjà chargés. Pour cela, vous devez utiliser le <xref:System.LoaderOptimizationAttribute> attribut, qui doit être appliqué à la méthode de point d’entrée (`Main`). Dans ce cas, utilisez uniquement du code pour implémenter votre définition d’application (consultez [Vue d’ensemble de la gestion d’applications](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.LoaderOptimizationAttribute>  
 [Compléments et extensibilité](../../../../docs/framework/add-ins/index.md)  
 [Domaines d’application](../../../../docs/framework/app-domains/application-domains.md)  
 [Vue d’ensemble de la communication à distance .NET framework](http://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Objets accessibles à distance](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/app-development/how-to-topics.md)
