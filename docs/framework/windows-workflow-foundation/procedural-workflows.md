---
title: "Workflows proc&#233;duraux | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Workflows proc&#233;duraux
Les workflows procéduraux utilisent des méthodes de contrôle de flux semblables à ceux recherchés dans les langages de procédures.Ces constructions comprennent notamment `While` et `If`.Ces workflows peuvent être composés librement à l'aide d'autres activités de contrôle de flux telles que <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Sequence>.  
  
## Contrôle du flux d'exécution  
 La bibliothèque d'activité de workflow a des activités pour modéliser la plupart des méthodes de contrôle de flux utilisé dans les langages de procédures.Ces composants sont les suivants :  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 Pour utiliser des activités de contrôle de flux, glissez\-les et déposez\-les depuis la boîte à outils **Activité** vers une activité composite à l'intérieur de la fenêtre du concepteur.  
  
> [!NOTE]
>  En cas d'utilisation de [!INCLUDE[dublin](../../../includes/dublin-md.md)] pour héberger les workflows sur une batterie de serveurs Web, AppFabric déplacera des instances entre différents serveurs AppFabric.Cela nécessite que les ressources puissent être partagées entre tous les nœuds.Aucune des activités de workflow .NET 4 par défaut ne contient des opérations qui ont accès à des ressources locales.Comme AppFabric n'offre aucun mécanisme pour marquer un workflow comme étant immuable, un développeur ne doit pas créer d'activités personnalisées qui échouent lorsqu'un workflow est déplacé.  
  
## Voir aussi  
 [Workflows d'organigramme](../../../docs/framework/windows-workflow-foundation//flowchart-workflows.md)