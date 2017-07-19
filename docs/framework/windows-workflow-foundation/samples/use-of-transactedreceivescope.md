---
title: "Utilisation de TransactedReceiveScope | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Utilisation de TransactedReceiveScope
Cet exemple montre comment passer une transaction d'un client à un serveur à l'aide de <xref:System.Activities.Statements.TransactionScope> pour créer une transaction sur le client et un <xref:System.ServiceModel.Activities.TransactedReceiveScope> pour recevoir un message avec une transaction passée et mesurer l'étendue de la durée de vie de la transaction sur le serveur.Cet exemple est composé deux projets qui jouent les rôles de client et serveur.  
  
## Application cliente  
 L'application cliente exécute un workflow qui imprime l'ID de transaction distribuée, envoie un message au serveur, passe la transaction, reçoit la réponse, imprime à nouveau l'ID de transaction distribuée et se termine.Lorsque l'ID de transaction distribuée est initialement imprimé, il s'agit d'un GUID vide, car la transaction est encore uniquement locale.  
  
## Application serveur  
 Le projet serveur est semblable ; toutefois, le workflow est hébergé dans <xref:System.ServiceModel.Activities.WorkflowServiceHost> parce qu'il doit écouter le message du client sur un point de terminaison.Le workflow est centré sur le <xref:System.ServiceModel.Activities.TransactedReceiveScope>, qui reçoit la transaction passée du client, imprime le message envoyé, imprime l'ID de transaction distribuée et envoie la réponse au client.L'ID de transaction distribuée est maintenant un GUID non vide et, si une activité prenant en charge les transactions a été ajoutée au corps du <xref:System.ServiceModel.Activities.TransactedReceiveScope>, elle s'exécute sous la transaction passée.  
  
#### Pour exécuter l'exemple  
  
1.  Ouvrez la solution TransactedReceiveScope.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B ou sélectionnez **Générer la solution** dans le menu **Générer**.  
  
3.  Une fois que la génération a réussi, cliquez avec le bouton droit sur la solution, puis sélectionnez **Définir les projets de démarrage**.Dans la boîte de dialogue, sélectionnez **Plusieurs projets de démarrage** et vérifiez que l'action pour les deux projets est **Démarrer**.  
  
4.  Appuyez sur F5 ou sélectionnez **Démarrer le débogage** dans le menu **Déboguer**.Vous pouvez également appuyer sur CTRL\+F5 ou sélectionner **Exécuter sans débogage** dans le menu **Déboguer** pour effectuer une exécution sans débogage.  
  
    > [!NOTE]
    >  Le serveur doit être en cours d'exécution avant de démarrer le client.La sortie de la fenêtre de console qui héberge le service indique le moment où il a démarré.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`  
  
## Voir aussi