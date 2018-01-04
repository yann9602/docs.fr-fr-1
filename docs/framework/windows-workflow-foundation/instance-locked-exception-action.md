---
title: "Action d'exception verrouillée d'instance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b221b0eef1e132789ef04fb59b56126f023bc43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="instance-locked-exception-action"></a>Action d'exception verrouillée d'instance
La propriété <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> du Magasin d'instances de workflow SQL vous permet de spécifier quelle mesure le fournisseur de persistance SQL doit prendre lorsqu'il reçoit une <xref:System.Runtime.DurableInstancing.InstanceLockedException>. Le fournisseur de persistance reçoit cette exception lorsqu'il essaye de verrouiller une instance de service de workflow actuellement verrouillée par un autre hôte de service. Les valeurs possibles pour cette propriété sont : <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> et <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. La valeur par défaut est <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. La liste suivante décrit ces trois options :  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. L’hôte de service ne tente pas de verrouiller l’instance de service de flux de travail et passe la <xref:System.Runtime.DurableInstancing.InstanceLockedException> à l’appelant.  Si votre flux de travail reste en mémoire pendant une durée supérieure à 60 secondes, utilisez <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> en tant que la nouvelle tentative. La valeur par défaut est <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>. L'hôte de service réessaie de verrouiller l'instance de service de workflow avec un intervalle de tentative linéaire et passe <xref:System.Runtime.DurableInstancing.InstanceLockedException> à l'appelant à la fin de la séquence. Si votre flux de travail reste dans la mémoire approximativement entre 5 et 60 secondes, et les messages arrivent par lot là où il est plus probable qu'ils soient envoyés à la même instance sur le même hôte pour traiter tous les messages avant de décharger le flux de travail, utilisez <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> pour obtenir la meilleure latence sans gaspiller de ressources.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. L'hôte de service réessaie de verrouiller l'instance de service de workflow avec un intervalle de tentative de réduction de puissance exponentiel et passe l'exception à l'appelant à la fin de la séquence. Si votre flux de travail reste en mémoire pendant une durée très courte (inférieure à 5 secondes), ou une batterie de serveurs Web a une grande taille et la probabilité qu'un autre message soit remis au même hôte n'est pas très élevée, utilisez <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> pour obtenir la meilleure latence.  
  
 La fonctionnalité Action d'exception verrouillée d'instance prend en charge les scénarios ci-après. Dans tous les scénarios, si la propriété instanceLockedExceptionAction du SqlWorkflowInstanceStore a la valeur <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> ou <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>, l'hôte réessaye de façon transparente d'acquérir régulièrement le verrou sur les instances.  
  
1.  **L’activation de l’arrêt approprié et le recyclage avec chevauchement des domaines d’application.** Supposons qu’un **AppDomain** avec un hôte de service exécutant des instances de service de flux de travail est en cours de recyclage de nouveaux **AppDomain** est affiché pour gérer les nouvelles requêtes en parallèle alors que l’ancien  **AppDomain** est arrêté correctement. L'arrêt attend jusqu'à ce que les instances de service de workflow soient inactives, puis il les rend persistantes et les décharge. Toute tentative d’hôtes dans le nouveau **AppDomain** de verrouiller une instance entraîne une <xref:System.Runtime.DurableInstancing.InstanceLockedException>.  
  
2.  **L’évolution horizontale du flux de travail durables parmi une batterie homogène de serveurs.** Imaginez qu'un nœud d'une batterie de serveurs sur laquelle une instance de workflow s'exécute tombe en panne et que l'hôte de workflow ne peut pas supprimer les verrous sur l'instance qu'il exécute. Lorsqu'un hôte de service s'exécutant sur un autre nœud de la batterie reçoit un message pour cette instance de workflow, il essaye d'acquérir des verrous sur ces instances et reçoit l'<xref:System.Runtime.DurableInstancing.InstanceLockedException>. Les verrous expirent après un certain temps, car l'hôte qui était censé renouveler le verrou n'existe plus.  
  
     **L’évolution horizontale du flux de travail durables parmi une batterie homogène de serveurs.**  Supposons que vous souhaitez étendre horizontalement un flux de travail durable à l’aide de plusieurs hôtes derrière un NLB (équilibrage de charge réseau), l’hôte de flux de travail en cours d’exécution sur un nœud de la batterie charge une instance de workflow et traite un message et le message suivant à l’instance est acheminé vers l’ordinateur hôte qui s’exécute sur un autre nœud, car l’équilibrage de charge réseau ne dispose pas de l’algorithme de routage pour remettre les messages à l’hôte qui est déjà en cours d’exécution l’instance. À la réception du message, le second hôte essaye de charger l'instance de workflow et reçoit l'objet <xref:System.Runtime.DurableInstancing.InstanceLockedException>, car le premier hôte a un verrou sur l'instance. Le premier hôte déverrouille l'instance lorsqu'il a terminé de traiter le premier message et le second hôte acquiert le verrou lorsqu'il réessaye une nouvelle fois. Il charge alors l'instance et traite le second message.
