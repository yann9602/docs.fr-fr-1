---
title: "Communication asynchrone | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Communication asynchrone
Cet exemple montre comment la communication entre deux services [!INCLUDE[wf](../../../../includes/wf-md.md)] différents s'effectue de façon asynchrone par défaut.  
  
## Démonstrations  
 Communication asynchrone entre des services [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  
  
## Discussion  
 Cet exemple montre comment la communication entre des applications [!INCLUDE[wf1](../../../../includes/wf1-md.md)] s'effectue de façon asynchrone à l'aide des activités de messagerie fournies par le .NET Framework.  
  
 Cet exemple est composé des trois projets suivants :  
  
 CreditCheckService  
 Ce service reçoit le niveau de crédit d'une personne particulière ou la valeur de l'élément à acquérir, puis décide si le crédit est accordé à la personne.  
  
 RentalApprovalService  
 Ce service reçoit une application d'une personne qui a besoin d'un crédit.Il communique de façon asynchrone avec `CreditCheckService` pour décider si l'application de crédit est valide.  
  
 Client  
 Le client communique de façon synchrone avec `RentalApprovalService` pour savoir si le crédit est approuvé.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Cliquez avec le bouton droit sur la solution **AsynchronousCommunication**, puis sélectionnez **Propriétés**.  
  
2.  Dans **Propriétés communes**, sélectionnez **Projet de démarrage**, puis **Plusieurs projets de démarrage**.  
  
3.  Déplacez **RentalApprovalService** en première position dans la liste, suivi de **CreditCheckService**, puis de **Client**.Définissez l'action de **démarrage** sur les trois projets.  
  
4.  Cliquez sur **OK**, puis appuyez sur F5 pour exécuter l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`