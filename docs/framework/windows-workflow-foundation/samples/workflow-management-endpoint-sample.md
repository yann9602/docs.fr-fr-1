---
title: "Exemple de point de terminaison de gestion de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Exemple de point de terminaison de gestion de workflow
Cet exemple montre comment un point de terminaison de contrôle de workflow peut être utilisé pour créer et exécuter des workflows à la fois localement et à distance.Il montre comment héberger un point de terminaison de contrôle et écrire des clients qui appellent le point de terminaison de contrôle pour créer et exécuter l'instance d'un workflow.Le workflow n'est pas un service.  
  
 Du côté service de l'exemple un workflow est hébergé avec WorkflowServiceHost et un WorkflowControlEndpoint est ajouté afin que les clients puissent exécuter des opérations de contrôle \(Suspendre, Démarrer, etc.\).Un CreationEndpoint défini par l'utilisateur est également ajouté pour permettre la création du workflow.Le service utilise ensuite ces points de terminaison pour démarrer le workflow dans un état suspendu, puis pour reprendre le workflow.Le client exécute les mêmes opérations mais à partir du code client.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] ces interfaces, consultez [Point de terminaison de contrôle de workflow](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) et [Procédure : héberger un workflow sans service dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### Pour exécuter l'exemple  
  
1.  Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des privilèges d'administrateur.  
  
2.  Ouvrez la solution ManagementEndpoint.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B ou sélectionnez **Générer la solution** dans le menu **Générer**.  
  
4.  Démarrez l'application ManagementEndpoint.exe.  
  
5.  Démarrez l'application Client.exe.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`  
  
## Voir aussi