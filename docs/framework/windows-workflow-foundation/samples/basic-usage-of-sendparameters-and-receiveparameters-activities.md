---
title: "Utilisation de base des activit&#233;s SendParameters et ReceiveParameters | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Utilisation de base des activit&#233;s SendParameters et ReceiveParameters
Cet exemple illustre l'utilisation des activités <xref:System.ServiceModel.Activities.SendParametersContent> et <xref:System.ServiceModel.Activities.ReceiveParametersContent>.Le service expose une opération qui accepte un argument de type chaîne et retourne l'entrée au client.L'exemple montre comment configurer les paramètres pour ces activités de messagerie.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### Utilisation de cet exemple  
  
1.  Chargez la solution du projet dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et générez le projet.  
  
2.  En premier lieu, exécutez l'application EchoWorkflowService, générée dans \[répertoire de base de la solution\]\\EchoWorkflowService\\bin\\debug.  
  
3.  En second lieu, exécutez l'application EchoWorkflowClient, générée dans \[répertoire de base de la solution\]\\EchoWorkflowClient\\bin\\debug.  
  
4.  Le client appelle l'opération Echo sur le service et imprime les résultats.Une fois cette opération terminée, appuyez sur ENTRÉE pour quitter le client, puis le service.  
  
## Voir aussi