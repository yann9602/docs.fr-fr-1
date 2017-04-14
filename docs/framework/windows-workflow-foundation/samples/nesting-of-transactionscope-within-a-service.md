---
title: "Imbrication de TransactionScope dans un service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Imbrication de TransactionScope dans un service
Cet exemple se compose de deux scénarios qui s'exécutent, en montrant comment gérer des instances d'activité <xref:System.Activities.Statements.TransactionScope> dans un service.En premier lieu, la transaction est initiée à l'aide de l'activité <xref:System.Activities.Statements.TransactionScope> pour créer une transaction sur le client et <xref:System.ServiceModel.Activities.TransactedReceiveScope> pour recevoir et mesurer l'étendue de la durée de vie de la transaction sur le serveur.Le premier scénario dans le service exécute une activité <xref:System.Activities.Statements.TransactionScope> secondaire pour illustrer l'imbrication des activités <xref:System.Activities.Statements.TransactionScope> dans le service.Le deuxième scénario montre comment les délais d'expiration sont respectés dans les activités <xref:System.Activities.Statements.TransactionScope> imbriquées.  
  
## Application cliente  
 L'application cliente exécute un workflow qui démarre une activité <xref:System.Activities.Statements.TransactionScope>, imprime l'ID de transaction distribuée, envoie un message au serveur, passe la transaction, reçoit la réponse, imprime à nouveau l'ID de transaction distribuée et se termine.Cette opération est effectuée une fois pour chaque scénario de service.  
  
## Application serveur  
 Le projet serveur est hébergé dans <xref:System.ServiceModel.Activities.WorkflowServiceHost>, ce qui crée le point de terminaison sur lequel écouter le message du client.Le workflow est centré sur le <xref:System.ServiceModel.Activities.TransactedReceiveScope>, qui reçoit la transaction passée du client, imprime l'ID de transaction distribuée, puis exécute une deuxième activité <xref:System.Activities.Statements.TransactionScope>.Dans le premier scénario, la transaction est effectuée avec succès.Dans le deuxième scénario, le corps de l'activité <xref:System.Activities.Statements.TransactionScope> est un délai de cinq secondes et le délai d'expiration de la transaction est défini à deux secondes.Lorsque la transaction expire, elle est abandonnée.  
  
#### Pour exécuter l'exemple  
  
1.  Ouvrez la solution TransactionServiceExample.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B ou sélectionnez **Générer la solution** dans le menu **Générer**.  
  
3.  Une fois que la génération a réussi, cliquez avec le bouton droit sur la solution, puis sélectionnez **Définir les projets de démarrage**.Dans la boîte de dialogue, sélectionnez **Plusieurs projets de démarrage** et vérifiez que l'action pour les deux projets est **Démarrer**.  
  
4.  Appuyez sur F5 ou sélectionnez **Démarrer le débogage** dans le menu **Déboguer**.Vous pouvez également appuyer sur CTRL\+F5 ou sélectionner **Exécuter sans débogage** dans le menu **Déboguer** pour effectuer une exécution sans débogage.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Transactions\TRSCompostability`