---
title: Persistance du workflow
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 769197b3f59c68c79f94c71c49ba4b1f4f98da2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-persistence"></a><span data-ttu-id="06459-102">Persistance du workflow</span><span class="sxs-lookup"><span data-stu-id="06459-102">Workflow Persistence</span></span>
<span data-ttu-id="06459-103">La persistance de workflow est la capture durable de l'état d'une instance de workflow, indépendamment des informations sur le processus ou l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="06459-103">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="06459-104">Cela permet d'abord de fournir, en cas de défaillance du système, un point connu de récupération de l'instance de workflow. Ensuite, la mémoire est conservée en déchargeant les instances de workflow qui ne fonctionnent pas activement. Enfin, l'état de l'instance de workflow peut être déplacé d'un nœud vers un autre dans une batterie de serveurs.</span><span class="sxs-lookup"><span data-stu-id="06459-104">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="06459-105">La persistance permet l'agilité de processus, l'évolutivité, la récupération en cas de défaillance et la capacité de gérer la mémoire plus efficacement.</span><span class="sxs-lookup"><span data-stu-id="06459-105">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="06459-106">Le processus de persistance inclut l'identification d'un point de persistance, la collecte des données à enregistrer et enfin, la délégation de la mémoire physique des données à un fournisseur de persistance.</span><span class="sxs-lookup"><span data-stu-id="06459-106">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="06459-107">Pour activer la persistance pour un flux de travail, vous devez associer un magasin d’instances le **WorkflowApplication** ou **WorkflowServiceHost** comme indiqué dans [Comment : activer la persistance pour Flux de travail et des Services de Workflow](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="06459-107">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="06459-108">Le **WorkflowApplication** et **WorkflowServiceHost** le magasin d’instances associé permet d’activer des instances de workflow persistantes dans un magasin de persistance et le chargement des instances de flux de travail dans mémoire basée sur les données d’instance de flux de travail stockées dans le magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="06459-108">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="06459-109">Le [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] est fourni avec le **SqlWorkflowInstanceStore** (classe), qui autorise la persistance des données et des métadonnées sur les instances de workflow dans une base de données SQL Server 2005 ou SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="06459-109">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="06459-110">Consultez [magasin d’instances de flux de travail de SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="06459-110">See [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="06459-111">Pour stocker et charger vos données spécifiques à l'application, ainsi que les informations sur l'instance de workflow, vous pouvez créer des participants de persistance qui étendent la classe <xref:System.Activities.Persistence.PersistenceParticipant>.</span><span class="sxs-lookup"><span data-stu-id="06459-111">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="06459-112">Un participant de persistance participe au processus de persistance pour les fins suivantes : enregistrer des données sérialisables personnalisées dans le magasin de persistance ; charger des données, du magasin d’instances vers la mémoire ; et effectuer toute logique supplémentaire dans le cadre d’une transaction de persistance.</span><span class="sxs-lookup"><span data-stu-id="06459-112">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="06459-113">Pour plus d’informations, consultez [Participants de persistance](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span><span class="sxs-lookup"><span data-stu-id="06459-113">For more information, see [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span></span>  
  
 <span data-ttu-id="06459-114">Windows Server AppFabric simplifie le processus de configuration de la persistance.</span><span class="sxs-lookup"><span data-stu-id="06459-114">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="06459-115">[Concepts de persistance avec Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201200)</span><span class="sxs-lookup"><span data-stu-id="06459-115"> [Persistence Concepts with Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="06459-116">Points de persistance implicites</span><span class="sxs-lookup"><span data-stu-id="06459-116">Implicit Persistence Points</span></span>  
 <span data-ttu-id="06459-117">La liste suivante comprend des exemples de conditions selon lesquelles un workflow est rendu persistant, lors de l'association d'un magasin d'instances à un workflow.</span><span class="sxs-lookup"><span data-stu-id="06459-117">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
-   <span data-ttu-id="06459-118">Lorsqu’un **TransactionScope** activité se termine ou un **TransactedReceiveScope** activité est terminée.</span><span class="sxs-lookup"><span data-stu-id="06459-118">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
-   <span data-ttu-id="06459-119">Lorsqu’une instance de workflow devienne inactive et le **WorkflowIdleBehavior** est définie sur l’ordinateur hôte de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="06459-119">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="06459-120">Cela se produit, par exemple, lorsque vous utilisez des activités de messagerie ou un **délai** activité.</span><span class="sxs-lookup"><span data-stu-id="06459-120">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
-   <span data-ttu-id="06459-121">Lorsqu’un WorkflowApplication devient inactif et le **PersistableIdle** de l’application est définie sur **PersistableIdleAction.Persist**.</span><span class="sxs-lookup"><span data-stu-id="06459-121">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
-   <span data-ttu-id="06459-122">Lorsqu'une application hôte a pour instruction de rendre persistante ou de décharger une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="06459-122">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
-   <span data-ttu-id="06459-123">Lorsqu'une instance de workflow est arrêtée ou prend fin.</span><span class="sxs-lookup"><span data-stu-id="06459-123">When a workflow instance is terminated or finishes.</span></span>  
  
-   <span data-ttu-id="06459-124">Lorsqu’un **Persist** activité s’exécute.</span><span class="sxs-lookup"><span data-stu-id="06459-124">When a **Persist** activity executes.</span></span>  
  
-   <span data-ttu-id="06459-125">Lorsqu'une instance d'un workflow développé à l'aide d'une version précédente de Windows Workflow Foundation rencontre un point de persistance lors de l'exécution interopérable.</span><span class="sxs-lookup"><span data-stu-id="06459-125">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06459-126">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="06459-126">In This Section</span></span>  
  
-   [<span data-ttu-id="06459-127">Magasin d’instances de workflow SQL</span><span class="sxs-lookup"><span data-stu-id="06459-127">SQL Workflow Instance Store</span></span>](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [<span data-ttu-id="06459-128">Magasins d’instances</span><span class="sxs-lookup"><span data-stu-id="06459-128">Instance Stores</span></span>](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [<span data-ttu-id="06459-129">Participants de persistance</span><span class="sxs-lookup"><span data-stu-id="06459-129">Persistence Participants</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [<span data-ttu-id="06459-130">Bonnes pratiques sur la persistance</span><span class="sxs-lookup"><span data-stu-id="06459-130">Persistence Best Practices</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [<span data-ttu-id="06459-131">Instances de workflow non persistantes</span><span class="sxs-lookup"><span data-stu-id="06459-131">Non-Persisted Workflow Instances</span></span>](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [<span data-ttu-id="06459-132">Suspension et reprise d’un workflow</span><span class="sxs-lookup"><span data-stu-id="06459-132">Pausing and Resuming a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
