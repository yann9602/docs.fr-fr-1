---
title: Vue d'ensemble des topologies de navigation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbe7fe80639537293413d8fb923033909a2451e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="navigation-topologies-overview"></a>Vue d'ensemble des topologies de navigation
<a name="introduction"></a>Cette présentation fournit une introduction aux topologies de navigation dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Trois topologies de navigation courantes, avec des exemples, sont abordées dans cet article.  
  
> [!NOTE]
>  Avant de lire cette rubrique, vous devez être familiarisé avec le concept de navigation structurée dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] à l’aide de fonctions de page. Pour plus d’informations sur les deux de ces rubriques, consultez [Structured Navigation Overview](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Topologies de navigation](#Navigation_Topologies)  
  
-   [Topologies de navigation structurée](#Structured_Navigation_Topologies)  
  
-   [Navigation sur une topologie linéaire fixe](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [Navigation dynamique sur une topologie hiérarchique fixe](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [Navigation sur une topologie générée de manière dynamique](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Topologies de navigation  
 Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation se compose généralement de pages (<xref:System.Windows.Controls.Page>) avec des liens hypertexte (<xref:System.Windows.Documents.Hyperlink>) qui naviguent jusqu'à d’autres pages lorsque vous cliquez sur. Les pages accédées sont identifiées par [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (consultez [URI à en-tête Pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)). Prenons l’exemple simple suivant qui affiche les pages, des liens hypertexte et [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Ces pages sont réorganisées dans une *topologie de navigation* dont la structure est déterminée par la façon dont vous pouvez naviguer entre les pages. Cette topologie de navigation particulière convient aux scénarios simples, bien que la navigation puisse nécessiter des topologies plus complexes, dont certaines peuvent être définies uniquement quand une application est en cours d’exécution.  
  
 Cette rubrique couvre trois topologies de navigation courantes : *linéaire fixe*, *hiérarchique fixe*, et *générés de manière dynamique*. Chaque topologie de navigation est illustrée par un exemple qui a un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] comme celui qui est indiqué dans l’illustration suivante :  
  
 ![Pages de tâches avec des éléments de données](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Topologies de navigation structurée  
 Il existe deux grands types de topologies de navigation :  
  
-   **Topologie fixe** : elle est définie au moment de la compilation et ne change pas au moment de l’exécution. Les topologies fixes sont utiles pour la navigation parmi une séquence fixe de pages dans un ordre linéaire ou hiérarchique.  
  
-   **Topologie dynamique** : elle est définie au moment de l’exécution en fonction des informations recueillies auprès de l’utilisateur, de l’application ou du système. Les topologies dynamiques sont utiles quand les pages peuvent être parcourues dans différentes séquences.  
  
 Bien qu’il soit possible de créer des topologies de navigation à l’aide de pages, les exemples utilisent des fonctions de page car elles fournissent une prise en charge supplémentaire qui simplifie la prise en charge de la transmission et du retour de données par l’intermédiaire des pages d’une topologie.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Navigation sur une topologie linéaire fixe  
 Une topologie linéaire fixe est analogue à la structure d’un Assistant qui a une ou plusieurs pages parcourues dans une séquence fixe. La figure suivante montre la structure et le flux de haut niveau d’un Assistant avec une topologie linéaire fixe.  
  
 ![Diagramme de topologie de navigation](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")  
  
 Les comportements types de navigation dans une topologie linéaire fixe sont les suivants :  
  
-   Navigation de la page appelante vers une page de lancement qui initialise l’Assistant et accède à sa première page. Une page de lancement (un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-moins <xref:System.Windows.Navigation.PageFunction%601>) n’est pas nécessaire, car une page appelante peut appeler directement à la première page de l’Assistant. Une page de lancement vous permet toutefois de simplifier l’initialisation de l’Assistant, en particulier si l’initialisation est complexe.  
  
-   Les utilisateurs peuvent naviguer parmi les pages à l’aide de boutons Précédent et Suivant (ou de liens hypertexte).  
  
-   Les utilisateurs peuvent naviguer parmi les pages à l’aide du journal.  
  
-   Les utilisateurs peuvent annuler l’Assistant à partir de n’importe laquelle de ses pages en appuyant sur un bouton Annuler.  
  
-   Les utilisateurs peuvent accepter l’Assistant dans sa dernière page en appuyant sur un bouton Terminer.  
  
-   Si un Assistant est annulé, il retourne un résultat approprié et ne retourne aucune donnée.  
  
-   Si un utilisateur accepte un Assistant, celui-ci retourne un résultat approprié et retourne les données recueillies.  
  
-   Une fois l’Assistant terminé (accepté ou annulé), les pages que comporte l’Assistant sont supprimées du journal. Ainsi, chaque instance de l’Assistant est isolée, ce qui évite les anomalies de données ou d’état potentielles.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Navigation dynamique sur une topologie hiérarchique fixe  
 Dans certaines applications, les pages autorisent la navigation vers plusieurs autres pages, comme illustré ci-dessous.  
  
 ![Une page qui autorise la navigation vers plusieurs pages](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")  
  
 Cette structure porte le nom de topologie hiérarchique fixe, et la séquence dans laquelle la hiérarchie est parcourue est souvent déterminée au moment de l’exécution par l’application ou l’utilisateur. Au moment de l’exécution, chaque page de la hiérarchie qui autorise la navigation vers plusieurs autres pages recueille les données nécessaires pour déterminer la page à atteindre. La figure suivante illustre l’une des différentes séquences de navigation possibles d’après la figure précédente.  
  
 ![Diagramme de topologie de navigation](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")  
  
 Bien que la séquence dans laquelle les pages d’une structure hiérarchique fixe sont parcourues soit déterminée au moment de l’exécution, l’expérience utilisateur est identique à celle d’une topologie linéaire fixe :  
  
-   Navigation de la page appelante vers une page de lancement qui initialise l’Assistant et accède à sa première page. Une page de lancement (un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-moins <xref:System.Windows.Navigation.PageFunction%601>) n’est pas nécessaire, car une page appelante peut appeler directement à la première page de l’Assistant. Une page de lancement vous permet toutefois de simplifier l’initialisation de l’Assistant, en particulier si l’initialisation est complexe.  
  
-   Les utilisateurs peuvent naviguer parmi les pages à l’aide de boutons Précédent et Suivant (ou de liens hypertexte).  
  
-   Les utilisateurs peuvent naviguer parmi les pages à l’aide du journal.  
  
-   Les utilisateurs peuvent changer la séquence de navigation s’ils reviennent en arrière dans le journal.  
  
-   Les utilisateurs peuvent annuler l’Assistant à partir de n’importe laquelle de ses pages en appuyant sur un bouton Annuler.  
  
-   Les utilisateurs peuvent accepter l’Assistant dans sa dernière page en appuyant sur un bouton Terminer.  
  
-   Si un Assistant est annulé, il retourne un résultat approprié et ne retourne aucune donnée.  
  
-   Si un utilisateur accepte un Assistant, celui-ci retourne un résultat approprié et retourne les données recueillies.  
  
-   Une fois l’Assistant terminé (accepté ou annulé), les pages que comporte l’Assistant sont supprimées du journal. Ainsi, chaque instance de l’Assistant est isolée, ce qui évite les anomalies de données ou d’état potentielles.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Navigation sur une topologie générée de manière dynamique  
 Dans certaines applications, la séquence dans laquelle plusieurs pages sont parcourues peut être déterminée uniquement au moment de l’exécution, que ce soit par l’utilisateur, par l’application ou par des données externes. La figure suivante illustre un ensemble de pages avec une séquence de navigation indéterminée.  
  
 ![Diagramme de topologie de navigation](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")  
  
 La figure suivante illustre une séquence de navigation qui a été choisie par l’utilisateur au moment de l’exécution.  
  
 ![Diagramme de navigation](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")  
  
 Cette séquence de navigation est une topologie générée de manière dynamique. Pour l’utilisateur, comme avec les autres topologies de navigation, l’expérience utilisateur est la même qu’avec les topologies précédentes :  
  
-   Navigation de la page appelante vers une page de lancement qui initialise l’Assistant et accède à sa première page. Une page de lancement (un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-moins <xref:System.Windows.Navigation.PageFunction%601>) n’est pas nécessaire, car une page appelante peut appeler directement à la première page de l’Assistant. Une page de lancement vous permet toutefois de simplifier l’initialisation de l’Assistant, en particulier si l’initialisation est complexe.  
  
-   Les utilisateurs peuvent naviguer parmi les pages à l’aide de boutons Précédent et Suivant (ou de liens hypertexte).  
  
-   Les utilisateurs peuvent naviguer parmi les pages à l’aide du journal.  
  
-   Les utilisateurs peuvent annuler l’Assistant à partir de n’importe laquelle de ses pages en appuyant sur un bouton Annuler.  
  
-   Les utilisateurs peuvent accepter l’Assistant dans sa dernière page en appuyant sur un bouton Terminer.  
  
-   Si un Assistant est annulé, il retourne un résultat approprié et ne retourne aucune donnée.  
  
-   Si un utilisateur accepte un Assistant, celui-ci retourne un résultat approprié et retourne les données recueillies.  
  
-   Une fois l’Assistant terminé (accepté ou annulé), les pages que comporte l’Assistant sont supprimées du journal. Ainsi, chaque instance de l’Assistant est isolée, ce qui évite les anomalies de données ou d’état potentielles.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Vue d’ensemble de la navigation structurée](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
