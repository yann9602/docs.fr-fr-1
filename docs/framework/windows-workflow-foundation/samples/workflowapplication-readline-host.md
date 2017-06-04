---
title: "H&#244;te ReadLine WorkflowApplication | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# H&#244;te ReadLine WorkflowApplication
Cet exemple est un hôte ReadLine générique.Vous pouvez charger et exécuter tout workflow à l'aide de l'activité `ReadLine` incluse \(ou d'autres activités semblables qui obtiennent des données à partir de signets repris avec les chaînes\).La sortie de l'activité `WriteLine` ou de tout élément qui écrit dans l'extension <xref:System.Activities.Statements.WriteLine.TextWriter%2A> est dirigée vers la fenêtre hôte.Lorsqu'une instance est inactive, les signets disponibles pour cette instance s'affichent dans une zone de liste déroulante.Si vous sélectionnez un signet, entrez un texte et appuyez sur le bouton de reprise de signet, l'exécution du workflow continue.Vous pouvez également annuler, abandonner ou arrêter un workflow sélectionné.La persistance est activée par défaut ; vous pouvez fermer et rouvrir hôte, et la liste des instances est remplie avec les instances stockées dans la base de données.Le suivi est utilisé pour générer des événements de niveau <xref:System.Activities.WorkflowApplication> pour l'hôte avec la possibilité d'ajouter un suivi détaillé au niveau de l'activité.  
  
## Détails de l'exemple  
 Il existe deux couches au niveau de cet hôte : la vue et le gestionnaire d'instance.La vue se compose des classes `WorkflowApplicationInfo` et `HostView`.Le modèle général pour cet hôte est que la classe `HostView` affiche les options disponibles à l'intention de l'utilisateur selon des objets `WorkflowApplicationInfo` qui restent relativement synchronisés avec les instances qu'ils représentent.La couche du gestionnaire d'instance se compose de la classe `WorkflowApplicationManager`, qui est le noyau de toutes les communications hôtes, de la classe `WorkflowDefinitionExtension`, qui rend la relation persistante entre une instance et la définition de programme avec laquelle elle a démarré, et de quelques autres classes.Le `HostView` appelle des opérations de contrôle sur le `WorkflowApplicationManager`.Ces appels sont en général asynchrones pour maintenir une interface utilisateur réactive.Lorsque les appels asynchrones sont terminés, le `WorkflowApplicationManager` retourne des appels dans la couche de la vue via une interface correctement définie \(`IHostView`\).La classe `HostView` distribue le plus souvent ces appels de la classe `WorkflowApplicationManager` vers le thread d'interface utilisateur.L'écriture de texte s'effectue dans des objets <xref:System.Activities.Statements.WriteLine.TextWriter%2A> thread\-safe fournis par la classe `HostView`.L'interface utilisateur n'est pas le seul élément qui génère des événements.Les objets <xref:System.Activities.WorkflowApplication> signalent également le `WorkflowApplicationManager` lorsqu'ils sont `Idle`, `Complete` ou `Aborted`, par exemple.La classe `WorkflowApplicationManager` envoie le thread d'événement en distribuant un travail de nettoyage ou de mise à jour à l'hôte.  
  
 L'enregistrement du fichier utilisé pour lancer un <xref:System.Activities.WorkflowApplication> est facilité par la classe `WorkflowDefinitionExtension`.Elle implémente l'interface <xref:System.Activities.Persistence.PersistenceIOParticipant> pour participer à la persistance et rendre persistant le chemin d'accès à la définition de workflow.  
  
 La méthode `WorkflowApplicationManager.Load` utilise le chemin d'accès stocké pour instancier les programmes de workflow obligatoires pour le chargement d'objets <xref:System.Activities.WorkflowApplication> non terminés.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Cet exemple requiert l'installation de SQL Express.SQL Express est fourni avec [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Ouvrez une invite de commandes de Visual Studio 2010.  
  
3.  Accédez au répertoire de l'exemple \(\\WF\\Basic\\Execution\\ControllingWorkflowApplications\) et exécutez CreateInstanceStore.cmd.  
  
4.  Le script CreateInstanceStore.cmd tente de créer la base de données sur l'instance par défaut de SQL Server 2008 Express.Si vous voulez installer la base de données sur une instance différente, modifiez le script en conséquence.  
  
5.  Compilez le projet WorkflowApplicationReadLineHost et exécutez\-le à partir de la ligne de commande.  
  
6.  Une fois en cours d'exécution, vous pouvez activer ou désactiver la persistance.En outre, vous avez également la possibilité d'activer ou de désactiver le suivi d'activité détaillé.  
  
7.  Appuyez sur le bouton de sélection en regard du bouton **Exécuter** pour rechercher un workflow défini dans un fichier XAML  
  
     Deux exemples se trouvent sous le dossier SampleWorkflows.L'exemple parallel1.xaml devient inactif.  
  
8.  Une fois un exemple sélectionné, appuyez sur le bouton **Exécuter**.  
  
9. Si ou lorsque le workflow devient inactif, la zone de liste déroulante **Signets** est remplie avec les signets disponibles.  
  
10. Les options sont à ce stade de reprendre un signet, d'annuler, d'abandonner ou de terminer le workflow.Vous pouvez également fermer l'hôte et le redémarrer.Si la persistance reste activée, les instances sont déchargées lors de l'arrêt et rechargées lors du démarrage.  
  
     Pour reprendre un signet, sélectionnez le signet voulu, tapez une valeur dans la zone de texte en regard de la zone de liste déroulante et cliquez sur **Reprendre le signet**.  
  
#### Pour supprimer la base de données du magasin d'instances  
  
1.  Ouvrez une invite de commandes de Visual Studio 2010.  
  
2.  Accédez au répertoire de l'exemple \(\\WF\\Basic\\Execution\\ControllingWorkflowApplications\) et exécutez RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`  
  
## Voir aussi