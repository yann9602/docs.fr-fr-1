---
title: "Persistance d&#39;une application de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Persistance d&#39;une application de workflow
Cet exemple montre comment exécuter un <xref:System.Activities.WorkflowApplication>, le décharger lorsqu'il devient inactif et le recharger pour continuer son exécution.  
  
## Détails de l'exemple  
 <xref:System.Activities.WorkflowApplication> est un hôte pour une instance de workflow unique qui fournit une interface simple et active certains des scénarios d'hébergement les plus courants.Un tel scénario est constitué de workflows de longue durée facilités par la persistance.Le contrôle hôte de persistance est effectué en appelant une opération de persistance sur le <xref:System.Activities.WorkflowApplication>, ou en gérant un événement <xref:System.Activities.WorkflowApplication> et en indiquant que le <xref:System.Activities.WorkflowApplication> doit être persistant.  
  
 L'exemple de workflow d est une activité <xref:System.Activities.Statements.WriteLine> qui invite l'utilisateur à entrer son nom, une activité `ReadLine` pour la réception du nom comme entrée via la reprise d'un <xref:System.Activities.Bookmark> et un autre <xref:System.Activities.Statements.WriteLine> pour retourner un message d'accueil à l'utilisateur.Lorsqu'un workflow attend une entrée, cela fournit un point naturel pour la persistance.Ce point est souvent désigné sous le nom de point <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent>.<xref:System.Activities.WorkflowApplication> déclenche l'événement <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent> chaque fois que le programme de workflow peut être rendu persistant, attend une reprise de signet et qu'aucun autre travail n'est effectué.Dans le workflow de cet exemple, ce point vient immédiatement après le début de l'exécution de l'activité `ReadLine`.  
  
 Un <xref:System.Activities.WorkflowApplication> est configuré pour effectuer des opérations de persistance avec un <xref:System.Runtime.Persistence.InstanceStore>.Cet exemple utilise <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.Le <xref:System.Runtime.Persistence.InstanceStore> doit être assigné à la propriété <xref:System.Activities.WorkflowApplication.InstanceStore%2A> avant l'exécution de <xref:System.Activities.WorkflowApplication>.  
  
 L'exemple ajoute un gestionnaire à l'événement <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>.Le gestionnaire de cet événement indique ce que le <xref:System.Activities.WorkflowApplication> doit faire en retournant un <xref:System.Activities.PersistableIdleAction>.Lorsque <xref:System.Activities.PersistableIdleAction> est retourné, le <xref:System.Activities.WorkflowApplication> est déchargé.  
  
 L'exemple accepte ensuite une entrée de l'utilisateur et charge le workflow persistant dans un nouveau <xref:System.Activities.WorkflowApplication>.Pour ce faire, il crée un <xref:System.Activities.WorkflowApplication>, recrée le <xref:System.Runtime.Persistence.InstanceStore> et associe les événements terminés et déchargés à l'instance, puis appelle <xref:System.Activities.WorkflowApplication.Load%2A> avec l'identificateur de l'instance de workflow cible.Une fois l'instance acquise, le signet de l'activité `ReadLine` est repris.Le workflow continue l'exécution à partir de l'activité `ReadLine` et s'exécute entièrement.Lorsque le workflow est terminé et déchargé, le <xref:System.Runtime.Persistence.InstanceStore> est appelé une dernière fois pour supprimer le workflow.  
  
#### Pour utiliser cet exemple  
  
1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
     Cet exemple requiert SQL Server Express, installé par défaut avec [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Accédez au répertoire de l'exemple \(\\WF\\Basic\\Persistence\\InstancePersistence\\CS\) et exécutez CreateInstanceStore.cmd.  
  
    > [!CAUTION]
    >  Le script CreateInstanceStore.cmd tente de créer la base de données sur l'instance par défaut de SQL Server 2008 Express.Si vous voulez installer la base de données sur une instance différente, modifiez le script en conséquence.  
  
3.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution Persistence.sln et appuyez sur Ctrl\+Maj\+B pour le générer.  
  
    > [!CAUTION]
    >  Si vous avez installé la base de données sur une instance autre que l'instance par défaut de SQL Server, mettez à jour la chaîne de connexion dans le code avant de générer la solution.  
  
4.  Exécutez l'exemple avec des privilèges d'administrateur. Pour ce faire, accédez au répertoire bin du projet \(\\WF\\Basic\\Persistence\\InstancePersistence\\bin\\Debug\) dans l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], cliquez avec le bouton droit sur Workflow.exe, puis sélectionnez **Exécuter en tant qu'administrateur**.  
  
#### Pour supprimer la base de données du magasin d'instances  
  
1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Accédez au répertoire de l'exemple et exécutez RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## Voir aussi  
 [Hébergement AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)