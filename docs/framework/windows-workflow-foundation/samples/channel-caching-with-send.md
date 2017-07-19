---
title: "Mise en cache des canaux avec Send | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Mise en cache des canaux avec Send
Le <xref:System.ServiceModel.Activities.SendMessageChannelCache> permet aux utilisateurs d'avoir différents niveaux de mise en cache des canaux avec les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.SendParametersContent>.La mise en cache au niveau de l'instance est activée par défaut et cet exemple illustre les fonctionnalités suivantes :  
  
1.  Partager un <xref:System.ServiceModel.Activities.SendMessageChannelCache> dans un domaine d'application.  
  
2.  Désactiver la mise en cache des canaux.  
  
3.  Partager un <xref:System.ServiceModel.Activities.SendMessageChannelCache> entre des instances de workflow dans un <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## Démonstrations  
 Extension <xref:System.ServiceModel.Activities.SendMessageChannelCache>, activités <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> et <xref:System.ServiceModel.Activities.SendReply>.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Chargez la solution du projet dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et générez le projet.  
  
2.  Exécutez l'application EchoWorkflowService générée dans \\EchoWorkflowService\\bin\\debug.  
  
3.  Exécutez l'application EchoWorkflowClient générée en .\\EchoWorkflowClient\\bin\\debug.  
  
4.  Le client appelle l'opération Echo sur le service et imprime les résultats.Lorsque les résultats ont été imprimés, appuyez sur ENTRÉE pour quitter le client et le service.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`