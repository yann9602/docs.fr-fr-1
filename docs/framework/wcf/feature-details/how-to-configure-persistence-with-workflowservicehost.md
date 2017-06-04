---
title: "Proc&#233;dure&#160;: configurer la persistance avec WorkflowServiceHost | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Proc&#233;dure&#160;: configurer la persistance avec WorkflowServiceHost
Cette rubrique décrit comment configurer la fonctionnalité de magasin d'instances de workflow SQL pour activer la persistance des workflows hébergés dans <xref:System.ServiceHost.Activities.WorkflowServiceHost> à l'aide d'un fichier de configuration.  Avant d'utiliser la fonctionnalité de magasin d'instances de workflow SQL, vous devez créer une base de données SQL utilisée pour rendre des instances de workflow persistantes.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Procédure : activer la persistance SQL pour les workflows et les services de workflow](../../../../docs/framework/windows-workflow-foundation//how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### Pour configurer le magasin d'instances de workflow SQL en mode Configuration  
  
1.  Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par configuration XML.  L'exemple de configuration suivant indique comment configurer le magasin d'instances de flux de travail SQL à l'aide de l'élément de comportement \<`sqlWorkflowInstanceStore`\> dans un fichier de configuration.  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la configuration du magasin d'instances de workflow SQL, consultez [Procédure : activer la persistance SQL pour les workflows et les services de workflow](../../../../docs/framework/windows-workflow-foundation//how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les différents paramètres pour l'élément de comportement \<`sqlWorkflowInstanceStore`\>, consultez [Magasin d'instances de workflow SQL](../../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md).  Windows Server App Fabric fournit son propre magasin de persistance.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Persistance de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193121)  
  
    > [!NOTE]
    >  L'exemple de configuration précédent utilise une configuration simplifiée.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### Pour configurer le magasin d'instances de workflow SQL en code  
  
1.  Les propriétés du magasin d'instances de workflow de SQL peuvent être configurées via le <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, un comportement de service qui vous permet de modifier les paramètres par code.  L'exemple suivant indique comment configurer le magasin d'instances de workflow SQL en utilisant l'élément de comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> dans un code.  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la configuration du magasin d'instances de workflow SQL, consultez [Procédure : activer la persistance SQL pour les workflows et les services de workflow](../../../../docs/framework/windows-workflow-foundation//how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les différents paramètres pour l'élément de comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, consultez [Magasin d'instances de workflow SQL](../../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md).  Windows Server App Fabric fournit son propre magasin de persistance.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Persistance de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193121)  
  
    > [!NOTE]
    >  L'exemple de configuration précédent utilise une configuration simplifiée.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Pour obtenir un exemple de configuration de la persistance par programme, consultez [Procédure : activer la persistance pour les workflows et les services de workflow](../../../../docs/framework/windows-workflow-foundation//how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [Persistance du workflow](../../../../docs/framework/windows-workflow-foundation//workflow-persistence.md)   
 [Persistance de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193121)