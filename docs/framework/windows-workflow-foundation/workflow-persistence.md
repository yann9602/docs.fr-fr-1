---
title: "Persistance du workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programmation [WF], persistance"
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# Persistance du workflow
La persistance de workflow est la capture durable de l'état d'une instance de workflow, indépendamment des informations sur le processus ou l'ordinateur.Cela permet d'abord de fournir, en cas de défaillance du système, un point connu de récupération de l'instance de workflow. Ensuite, la mémoire est conservée en déchargeant les instances de workflow qui ne fonctionnent pas activement. Enfin, l'état de l'instance de workflow peut être déplacé d'un nœud vers un autre dans une batterie de serveurs.  
  
 La persistance permet l'agilité de processus, l'évolutivité, la récupération en cas de défaillance et la capacité de gérer la mémoire plus efficacement.Le processus de persistance inclut l'identification d'un point de persistance, la collecte des données à enregistrer et enfin, la délégation de la mémoire physique des données à un fournisseur de persistance.  
  
 Pour activer la persistance pour un flux de travail, vous devez associer un magasin d'instances à la **WorkflowApplication** ou au **WorkflowServiceHost**, comme indiqué dans [Procédure : activer la persistance pour les workflows et les services de workflow](../../../docs/framework/windows-workflow-foundation//how-to-enable-persistence-for-workflows-and-workflow-services.md).La **WorkflowApplication** et le **WorkflowServiceHost** utilisent le magasin d'instances qui leur est associé pour activer d'une part la persistance d'instances de workflow dans un magasin de persistance et d'autre part, le chargement d'instances de workflow en mémoire, en fonction des données de l'instance de workflow stockées dans le magasin de persistance.  
  
 Le [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] est fourni avec la classe **SqlWorkflowInstanceStore** qui autorise la persistance de données et métadonnées sur les instances de workflow dans une base de données SQL Server 2005 ou SQL Server 2008.Pour plus d'informations, consultez [Magasin d'instances de workflow SQL](../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md).  
  
 Pour stocker et charger vos données spécifiques à l'application, ainsi que les informations sur l'instance de workflow, vous pouvez créer des participants de persistance qui étendent la classe <xref:System.Activities.Persistence.PersistenceParticipant>.Un participant de persistance participe au processus de persistance pour les fins suivantes : enregistrer des données sérialisables personnalisées dans le magasin de persistance ; charger des données, du magasin d'instances vers la mémoire ; et effectuer toute logique supplémentaire dans le cadre d'une transaction de persistance.Pour plus d'informations, consultez [Participants de persistance](../../../docs/framework/windows-workflow-foundation//persistence-participants.md).  
  
 Windows Server AppFabric simplifie le processus de configuration de la persistance.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Concepts de persistance avec Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## Points de persistance implicites  
 La liste suivante comprend des exemples de conditions selon lesquelles un workflow est rendu persistant, lors de l'association d'un magasin d'instances à un workflow.  
  
-   Lorsqu'une activité **TransactionScope** se termine ou qu'une activité **TransactedReceiveScope** se termine.  
  
-   Lorsqu'une instance de workflow devient inactive et que **WorkflowIdleBehavior** est défini sur l'hôte du workflow.Cela se produit, par exemple, lorsque vous utilisez des activités de messagerie ou une activité **Delay**.  
  
-   Lorsqu'un WorkflowApplication devient inactif et la propriété **PersistableIdle** de l'application a la valeur **PersistableIdleAction.Persist**.  
  
-   Lorsqu'une application hôte a pour instruction de rendre persistante ou de décharger une instance de workflow.  
  
-   Lorsqu'une instance de workflow est arrêtée ou prend fin.  
  
-   Lorsqu'une activité **Persist** s'exécute.  
  
-   Lorsqu'une instance d'un workflow développé à l'aide d'une version précédente de Windows Workflow Foundation rencontre un point de persistance lors de l'exécution interopérable.  
  
## Dans cette section  
  
-   [Magasin d'instances de workflow SQL](../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)  
  
-   [Magasins d'instances](../../../docs/framework/windows-workflow-foundation//instance-stores.md)  
  
-   [Participants de persistance](../../../docs/framework/windows-workflow-foundation//persistence-participants.md)  
  
-   [Meilleures pratiques de persistance](../../../docs/framework/windows-workflow-foundation//persistence-best-practices.md)  
  
-   [Instances de workflow non persistantes](../../../docs/framework/windows-workflow-foundation//non-persisted-workflow-instances.md)  
  
-   [Suspension et reprise d'un workflow](../../../docs/framework/windows-workflow-foundation//pausing-and-resuming-a-workflow.md)