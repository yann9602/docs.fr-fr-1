---
title: "Workflows procéduraux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd879d138a95c003ca0ffb12b3ce010534c3e158
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="procedural-workflows"></a>Workflows procéduraux
Les workflows procéduraux utilisent des méthodes de contrôle de flux semblables à ceux recherchés dans les langages de procédures. Ces constructions comprennent notamment `While` et `If`. Ces workflows peuvent être composés librement à l'aide d'autres activités de contrôle de flux telles que <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Contrôle du flux d'exécution  
 La bibliothèque d'activité de workflow a des activités pour modéliser la plupart des méthodes de contrôle de flux utilisé dans les langages de procédures. Elles incluent notamment :  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 Pour utiliser les activités de flux de contrôle, faites glisser et déposez les à partir de la **activité** boîte à outils dans une activité composite à l’intérieur de la fenêtre du concepteur.  
  
> [!NOTE]
>  En cas d'utilisation de [!INCLUDE[dublin](../../../includes/dublin-md.md)] pour héberger les workflows sur une batterie de serveurs Web, AppFabric déplacera des instances entre différents serveurs AppFabric. Cela nécessite que les ressources puissent être partagées entre tous les nœuds.  Aucune des activités de workflow .NET 4 par défaut ne contient des opérations qui ont accès à des ressources locales. Comme AppFabric n'offre aucun mécanisme pour marquer un workflow comme étant immuable, un développeur ne doit pas créer d'activités personnalisées qui échouent lorsqu'un workflow est déplacé.  
  
## <a name="see-also"></a>Voir aussi  
 [Workflows d’organigramme](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
