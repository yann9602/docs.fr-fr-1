---
title: "Gestion de l&#39;instance interrompue | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Gestion de l&#39;instance interrompue
Cet exemple montre comment gérer des instances de workflow qui ont été interrompues.L'action par défaut pour <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> est `AbandonAndSuspend`.Cela signifie que, par défaut, les exceptions non gérées levées à partir d'une instance de workflow hébergée dans le <xref:System.ServiceModel.WorkflowServiceHost> provoqueront la suppression de l'instance de la mémoire \(abandon\), et la version durable\/persistante de l'instance sera marquée comme interrompue.Une instance de workflow interrompue ne sera pas en mesure de fonctionner tant que l'interruption n'a pas été annulée.  
  
 L'exemple montre comment un utilitaire en ligne de commande peut être implémenté pour rechercher des instances interrompues et comment permettre à l'utilisateur de reprendre ou de terminer l'instance.Dans cet exemple, un service de workflow lève une exception intentionnellement, ce qui provoque son interruption.L'utilitaire en ligne de command peut ensuite être utilisé pour rechercher l'instance et, par la suite, la reprendre ou la terminer.  
  
## Démonstrations  
 <xref:System.ServiceModel.WorkflowServiceHost> avec <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> et <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> dans [!INCLUDE[wf](../../../../includes/wf-md.md)].  
  
## Discussion  
 L'utilitaire en ligne de commande implémenté dans cet exemple est spécifique à l'implémentation du magasin d'instances SQL fournie dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].Si vous avez une implémentation personnalisée du magasin d'instances, vous pouvez adapter cet utilitaire en remplaçant les implémentations `WorkflowInstanceCommand` dans l'exemple par des implémentations qui sont spécifiques à votre magasin d'instances.  
  
 L'implémentation fournie exécute directement des commandes SQL dans le magasin d'instances SQL pour répertorier les instances interrompues et s'appuie sur un <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> ajouté au <xref:System.ServiceModel.WorkflowServiceHost> pour reprendre ou terminer les instances.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Cet exemple requiert que les composants Windows suivants soient activés :  
  
    1.  Serveur de file d'attente Microsoft Message Queue \(MSMQ\)  
  
    2.  SQL Server Express  
  
2.  Configurez la base de données SQL Server.  
  
    1.  À partir d'une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], exécutez « setup.cmd » dans le répertoire de l'exemple SuspendedInstanceManagement, qui effectue les opérations suivantes :  
  
        1.  Crée une base de données de persistance à l'aide de SQL Server Express.Si la base de données de persistance existe déjà, elle est supprimée et recréée.  
  
        2.  Configure la base de données pour la persistance.  
  
        3.  Ajoute IIS APPPOOL\\DefaultAppPool et NT AUTHORITY\\Network Service au rôle InstanceStoreUsers qui a été défini lors de la configuration de la base de données pour la persistance.  
  
3.  Configurez la file d'attente de service.  
  
    1.  Dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], cliquez avec le bouton droit sur le projet **SampleWorkflowApp** et cliquez sur **Définir comme projet de démarrage**.  
  
    2.  Compilez et exécutez SampleWorkflowApp en appuyant sur **F5**.La file d'attente requise sera ainsi créée.  
  
    3.  Appuyez sur **Entrée** pour arrêter SampleWorkflowApp.  
  
    4.  Ouvrez la console Gestion de l'ordinateur en exécutant Compmgmt.msc à partir d'une invite de commandes.  
  
    5.  Développez **Services et applications**, **Message Queuing**, **Files d'attente privées**.  
  
    6.  Cliquez avec le bouton droit sur la file d'attente **ReceiveTx** et sélectionnez **Propriétés**.  
  
    7.  Sélectionnez l'onglet **Sécurité** et permettez à **Tout le monde** d'avoir des autorisations de **Recevoir un message**, **Lire le message** et **Envoyer un message**.  
  
4.  Exécutez maintenant l'exemple.  
  
    1.  Dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], exécutez à nouveau le projet SampleWorkflowApp sans déboguer en appuyant sur **Ctrl\+F5**.Deux adresses de point de terminaison seront imprimées dans la fenêtre de console : une pour le point de terminaison d'application et l'autre pour le <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.Une instance de workflow est ensuite créée et les enregistrements de suivi pour cette instance s'afficheront dans la fenêtre de console.L'instance de workflow lèvera une exception qui provoquera l'interruption et l'abandon de l'instance.  
  
    2.  L'utilitaire en ligne de commande peut ensuite être utilisé pour entreprendre des actions supplémentaires sur chacune de ces instances.La syntaxe pour les arguments de ligne de commande est la suivante :  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         Les commandes prises en charge sont `Query`, `Resume` et `Terminate`.Le commutateur InstanceId est uniquement obligatoire pour les opérations `Resume` et `Terminate`.  
  
#### Pour effectuer un nettoyage \(facultatif\)  
  
1.  Ouvrez la console Gestion de l'ordinateur en exécutant Compmgmt.msc à partir d'une invite de commandes `vs2010`.  
  
2.  Développez **Services et applications**, **Message Queuing**, **Files d'attente privées**.  
  
3.  Supprimez la file d'attente **ReceiveTx**.  
  
4.  Pour supprimer la base de données de persistance, exécutez cleanup.cmd.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`