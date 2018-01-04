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
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Procédure : configurer la persistance avec WorkflowServiceHost
Cette rubrique décrit comment configurer la fonctionnalité de magasin d'instances de workflow SQL pour activer la persistance des workflows hébergés dans <xref:System.ServiceModel.Activities.WorkflowServiceHost> à l'aide d'un fichier de configuration. Avant d’utiliser la fonctionnalité de magasin d’instances de workflow SQL, vous devez créer une base de données SQL utilisée pour rendre des instances de workflow persistantes. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : activer la persistance pour les Workflows et Services de Workflow SQL](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Pour configurer le magasin d'instances de workflow SQL en mode Configuration  
  
1.  Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par configuration XML. L'exemple de configuration suivant indique comment configurer le magasin d'instances de flux de travail SQL à l'aide de l'élément de comportement <`sqlWorkflowInstanceStore`> dans un fichier de configuration.  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]comment configurer le magasin d’instances de workflow SQL, consultez [Comment : activer de persistance SQL pour les Workflows et Services de Workflow](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les paramètres individuels pour le <`sqlWorkflowInstanceStore`> élément de comportement, consultez [magasin d’instances de flux de travail de SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric fournit son propre magasin de persistance. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Persistance de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  L'exemple de configuration précédent utilise une configuration simplifiée. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Simplifié la Configuration](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Pour configurer le magasin d'instances de workflow SQL en code  
  
1.  Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par code. L'exemple suivant indique comment configurer le magasin d'instances de workflow SQL en utilisant l'élément de comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> dans un code.  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]comment configurer le magasin d’instances de workflow SQL, consultez [Comment : activer de persistance SQL pour les Workflows et Services de Workflow](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les paramètres individuels pour le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> élément de comportement, consultez [magasin d’instances de flux de travail de SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric fournit son propre magasin de persistance. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Persistance de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  L'exemple de configuration précédent utilise une configuration simplifiée. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Simplifié la Configuration](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Pour obtenir un exemple montrant comment configurer la persistance par programme, consultez [Comment : activer la persistance pour les Workflows et Services de Workflow](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Persistance du workflow](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Persistance de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193121)
