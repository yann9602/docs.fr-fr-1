---
title: "Envoi et gestion des erreurs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Envoi et gestion des erreurs
Cet exemple montre comment utiliser les activités de messagerie <xref:System.ServiceModel.Activities.ReceiveReply> et <xref:System.ServiceModel.Activities.SendReply> pour envoyer et recevoir des erreurs attendues et inattendues.Dans ce scénario, la première demande du client génère une erreur attendue qui a été incluse dans sa collection <xref:System.ServiceModel.Activities.Send.KnownTypes%2A>.Les demandes suivantes du client entrainent la réception d'erreurs inattendues, avant que la dernière demande réussisse.  
  
## Pour utiliser cet exemple  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations élevées, en cliquant avec le bouton droit sur l'icône de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et en sélectionnant **Exécuter en tant qu'administrateur**.  
  
2.  Ouvrez le fichier solution Faults.sln.  
  
3.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
4.  Exécutez le projet de service.  
  
    1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet `FaultService`, puis sélectionnez **Définir comme projet de démarrage**.  
  
    2.  Appuyez sur CTRL\+F5.  
  
5.  Ouvrez une autre copie de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations élevées, en cliquant avec le bouton droit sur l'icône de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et en sélectionnant **Exécuter en tant qu'administrateur**.  
  
6.  Ouvrez le fichier solution Faults.sln.  
  
7.  Exécutez le projet client.  
  
    1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet `FaultClient`, puis sélectionnez **Définir comme projet de démarrage**.  
  
    2.  Appuyez sur CTRL\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Services\Faults`  
  
## Voir aussi