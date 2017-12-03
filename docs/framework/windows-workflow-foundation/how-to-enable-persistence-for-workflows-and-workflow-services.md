---
title: "Procédure : activer la persistance pour les workflows et les services de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1db45ecad833c4c05ba240569da9c85271e0b69e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Procédure : activer la persistance pour les workflows et les services de workflow
Cette rubrique décrit la procédure d'activation de la persistance pour les flux de travail et les services de workflow.  
  
## <a name="enable-persistence-for-workflows"></a>Activation de la persistance pour les flux de travail  
 Vous pouvez associer un magasin d’instances avec un **WorkflowApplication** à l’aide de la <xref:System.Activities.WorkflowApplication.InstanceStore%2A> propriété de la <xref:System.Activities.WorkflowApplication> classe. La méthode <xref:System.Activities.WorkflowApplication.Persist%2A> enregistre ou rend persistant un flux de travail dans le magasin d'instances associé à l'application. La méthode <xref:System.Activities.WorkflowApplication.Unload%2A> rend persistant un flux de travail dans le magasin d'instances, puis décharge l'instance de la mémoire. Le **charge** méthode charge un flux de travail en mémoire à l’aide des données de workflow stockées dans le magasin de persistance d’instance.  
  
 Le **Persist** méthode effectue les étapes suivantes :  
  
1.  Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.  
  
2.  Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.  
  
3.  Reprend le service de planification de workflow.  
  
 Le **Unload** méthode effectue les étapes suivantes :  
  
1.  Suspend le service de planification de workflow et attend jusqu'à ce que le flux de travail entre en état d'inactivité.  
  
2.  Rend le flux de travail persistant ou l'enregistre dans le magasin de persistance.  
  
3.  Supprime l'instance de workflow en mémoire.  
  
 Les deux le **Persist** et **Unload** méthodes se bloquent pendant un flux de travail est dans une zone de non-persistance jusqu'à ce que le flux de travail quitte la zone sans persistance. La méthode poursuit les opérations de persistance ou de déchargement une fois la zone sans persistance fermée. Si la zone sans persistance ne se ferme pas avant que le délai d'attente ne s'écoule ou si le processus de persistance prend trop de temps, une TimeoutException est levée.  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>Activation de la persistance pour les services de workflow dans le code  
 Le **DurableInstancingOptions** membre de la <xref:System.ServiceModel.WorkflowServiceHost> classe a une propriété nommée **InstanceStore** que vous pouvez utiliser pour associer un magasin d’instances le **WorkflowServiceHost** .  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 Lorsque le **WorkflowServiceHost** est ouvert, la persistance est automatiquement activée si le **DurableInstancingOptions.InstanceStore** n’est pas null.  
  
 En règle générale, un comportement de service fournit le magasin d’instances concrètes à utiliser avec un hôte de service de flux de travail à l’aide de la **InstanceStore** propriété. Par exemple, le SqlWorkflowInstanceStoreBehavior crée une instance de la **SqlWorkflowInstanceStore**, configure et l’assigne à la **DurableInstancingOptions.InstanceStore**.  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Activation de la persistance pour les services de workflow à l'aide d'un fichier de configuration d'application  
 La persistance peut être activée à l'aide d'un fichier de configuration de l'application en ajoutant le code suivant à votre fichier app.config ou web.config :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
