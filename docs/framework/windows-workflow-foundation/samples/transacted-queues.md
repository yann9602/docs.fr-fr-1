---
title: "Files d&#39;attente avec transaction | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Files d&#39;attente avec transaction
Cet exemple montre comment intégrer des files d'attente et des transactions dans [!INCLUDE[wf](../../../../includes/wf-md.md)] pour créer des services fiables et évolutifs.Un <xref:System.Activities.TransactionScope> est utilisé dans le workflow client pour envoyer un message à une file d'attente sous une transaction à l'aide du <xref:System.ServiceModel.NetMsmqBinding>.Un <xref:System.ServiceModel.Activities.TransactedReceiveScope> est utilisé sur le serveur pour recevoir des messages de la file d'attente et mettre à jour l'état du workflow sous la même transaction.  
  
## Démonstrations  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive> et corrélation basée sur le contenu.  
  
## Discussion  
 Pour illustrer les fonctionnalités couvertes dans cet exemple, un service de workflow `RewardsPoints` est créé, qui assure le suivi des points gagnés et utilisés pour un compte donné.Le client utilise <xref:System.Activities.WorkflowInvoker> pour simuler la publication de différentes demandes dans la file d'attente.Pour publier un message dans la file d'attente sous une transaction, l'activité <xref:System.ServiceModel.Activities.Send> peut être placée à l'intérieur du <xref:System.Activities.Statements.TransactionScope.Body%2A> d'un <xref:System.Activities.Statements.TransactionScope>.Dans cet exemple, le client s'exécute en premier, suivi par le serveur, pour montrer comment les messages en file d'attente peuvent découpler les applications serveur et cliente.  
  
 Une fois que le client est terminé, le service est configuré et hébergé.Dès qu'il s'ouvre, il démarre le traitement des messages qui ont déjà été placés dans la file d'attente.Chaque message est reçu et traité sous la même transaction de serveur.Dans cet exemple, le premier message reçu est une demande `CreateAccount` qui crée l'instance et initialise la corrélation de contenu selon le nom du compte passé dans le cadre du message de demande.Pour modéliser le type de service que vous pouvez attendre dans le monde réel, les deux activités <xref:System.ServiceModel.Activities.TransactedReceiveScope> suivantes qui traitent les messages `UsePoints` et `AddPoints` sont placées dans des branches parallèles dans une boucle `while` afin qu'elles puissent traiter à plusieurs reprises ces messages dans n'importe quel ordre.  
  
 <xref:System.Activities.Statements.TransactionScope> et <xref:System.ServiceModel.Activities.TransactedReceiveScope> ayant chacun un point de persistance implicite à la fin de leurs portées, l'utilisation de ces activités dans [!INCLUDE[wf1](../../../../includes/wf1-md.md)] combinée avec les files d'attente est une façon fiable de déplacer votre workflow d'un état cohérent vers le suivant, tout en s'assurant que les messages ne sont jamais perdus.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Installez et configurez MSMQ.Pour plus d'informations, consultez [Installation de Message Queuing \(MSMQ\)](http://go.microsoft.com/fwlink/?LinkId=178526).  
  
2.  Vérifiez que MSDTC fonctionne en exécutant la commande suivante sur une ligne de commande.`net start msdtc`  
  
3.  Compilez le projet et ouvrez le fichier exécutable ou ouvrez le projet dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et sélectionnez une option de démarrage dans le menu de débogage.En premier lieu, la file d'attente est créée, puis le client est exécuté et publie des messages dans la file d'attente et, enfin, le service démarre et les messages sont traités.Pour quitter le programme, appuyez sur ENTRÉE.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`