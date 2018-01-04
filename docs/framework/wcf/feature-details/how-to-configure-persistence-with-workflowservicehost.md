---
title: "Procédure : configurer la persistance avec WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41211eb1d104e0e540e257cffd4647c6fff9fb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="2d5c0-102">Procédure : configurer la persistance avec WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="2d5c0-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="2d5c0-103">Cette rubrique décrit comment configurer la fonctionnalité de magasin d'instances de workflow SQL pour activer la persistance des workflows hébergés dans <xref:System.ServiceModel.Activities.WorkflowServiceHost> à l'aide d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="2d5c0-104">Avant d’utiliser la fonctionnalité de magasin d’instances de workflow SQL, vous devez créer une base de données SQL utilisée pour rendre des instances de workflow persistantes.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2d5c0-105">[Comment : activer la persistance pour les Workflows et Services de Workflow SQL](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="2d5c0-105"> [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="2d5c0-106">Pour configurer le magasin d'instances de workflow SQL en mode Configuration</span><span class="sxs-lookup"><span data-stu-id="2d5c0-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1.  <span data-ttu-id="2d5c0-107">Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par configuration XML.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="2d5c0-108">L'exemple de configuration suivant indique comment configurer le magasin d'instances de flux de travail SQL à l'aide de l'élément de comportement <`sqlWorkflowInstanceStore`> dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore   
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"   
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2d5c0-109">comment configurer le magasin d’instances de workflow SQL, consultez [Comment : activer de persistance SQL pour les Workflows et Services de Workflow](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="2d5c0-109"> how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2d5c0-110">les paramètres individuels pour le <`sqlWorkflowInstanceStore`> élément de comportement, consultez [magasin d’instances de flux de travail de SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="2d5c0-110"> the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="2d5c0-111">Windows Server App Fabric fournit son propre magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-111">Windows Server App Fabric provides its own persistence store.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2d5c0-112">[Persistance de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="2d5c0-112"> [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2d5c0-113">L'exemple de configuration précédent utilise une configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-113">The preceding configuration example uses simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2d5c0-114">[Simplifié la Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="2d5c0-114"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="2d5c0-115">Pour configurer le magasin d'instances de workflow SQL en code</span><span class="sxs-lookup"><span data-stu-id="2d5c0-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1.  <span data-ttu-id="2d5c0-116">Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par code.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="2d5c0-117">L'exemple suivant indique comment configurer le magasin d'instances de workflow SQL en utilisant l'élément de comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> dans un code.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2d5c0-118">comment configurer le magasin d’instances de workflow SQL, consultez [Comment : activer de persistance SQL pour les Workflows et Services de Workflow](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="2d5c0-118"> how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2d5c0-119">les paramètres individuels pour le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> élément de comportement, consultez [magasin d’instances de flux de travail de SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="2d5c0-119"> the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="2d5c0-120">Windows Server App Fabric fournit son propre magasin de persistance.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-120">Windows Server App Fabric provides its own persistence store.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2d5c0-121">[Persistance de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="2d5c0-121"> [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2d5c0-122">L'exemple de configuration précédent utilise une configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="2d5c0-122">The preceding configuration example uses simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2d5c0-123">[Simplifié la Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="2d5c0-123"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="2d5c0-124">Pour obtenir un exemple montrant comment configurer la persistance par programme, consultez [Comment : activer la persistance pour les Workflows et Services de Workflow](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="2d5c0-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5c0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d5c0-125">See Also</span></span>  
 [<span data-ttu-id="2d5c0-126">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="2d5c0-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="2d5c0-127">Persistance du workflow</span><span class="sxs-lookup"><span data-stu-id="2d5c0-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="2d5c0-128">Persistance de Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="2d5c0-128">Windows Server App Fabric Persistence</span></span>](http://go.microsoft.com/fwlink/?LinkId=193121)
