---
title: "Proc&#233;dure&#160;: activer la persistance pour les workflows et les services de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Proc&#233;dure&#160;: activer la persistance pour les workflows et les services de workflow
Cette rubrique décrit la procédure d'activation de la persistance pour les flux de travail et les services de workflow.  
  
## Activation de la persistance pour les flux de travail  
 Vous pouvez associer un magasin d'instances à une **WorkflowApplication** à l'aide de la propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> de la classe <xref:System.Activities.WorkflowApplication>.La méthode <xref:System.Activities.WorkflowApplication.Persist%2A> enregistre ou rend persistant un flux de travail dans le magasin d'instances associé à l'application.La méthode <xref:System.Activities.WorkflowApplication.Unload%2A> rend persistant un flux de travail dans le magasin d'instances, puis décharge l'instance de la mémoire.La méthode **Load** charge un flux de travail en mémoire, à l'aide des données de workflow stockées dans le magasin de persistance d'instances.  
  
 La méthode **Persist** effectue les étapes suivantes :  
  
1.  Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.  
  
2.  Rend persistant le flux de travail ou l'enregistre dans le magasin de persistance.  
  
3.  Reprend le service de planification de workflow.  
  
 La méthode **Unload** effectue les étapes suivantes :  
  
1.  Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.  
  
2.  Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.  
  
3.  Supprime l'instance de workflow en mémoire.  
  
 Les méthodes **Persist** et **Unload** se bloquent toutes les deux lorsqu'un flux de travail est en zone sans persistance, et ce jusqu'à ce qu'il la quitte.La méthode poursuit les opérations de persistance ou de déchargement une fois la zone sans persistance fermée.Si la zone sans persistance ne se ferme pas avant que le délai d'attente ne s'écoule ou si le processus de persistance prend trop de temps, une TimeoutException est levée.  
  
## Activation de la persistance pour les services de workflow dans le code  
 Le membre **DurableInstancingOptions** de la classe <xref:System.ServiceModel.WorkflowServiceHost> a une propriété nommée **InstanceStore** que vous pouvez utiliser pour associer un magasin d'instances au **WorkflowServiceHost**.  
  
```  
  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
  
```  
  
 Une fois le **WorkflowServiceHost** ouvert, la persistance est activée automatiquement si le **DurableInstancingOptions.InstanceStore** n'est pas null.  
  
 En général, un comportement de service fournit le magasin d'instances concrètes à utiliser avec un hôte de service de workflow, à l'aide de la propriété **InstanceStore**.Par exemple, le SqlWorkflowInstanceStoreBehavior crée une instance du **SqlWorkflowInstanceStore**, la configure et l'affecte au **DurableInstancingOptions.InstanceStore**.  
  
## Activation de la persistance pour les services de workflow à l'aide d'un fichier de configuration d'application  
 La persistance peut être activée à l'aide d'un fichier de configuration de l'application en ajoutant le code suivant à votre fichier app.config ou web.config :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name=”myBehavior”>  
          <SqlWorkflowInstanceStore connectionString=”Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase”>  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
  
```