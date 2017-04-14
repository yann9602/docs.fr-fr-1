---
title: "D&#233;termination de la dur&#233;e d&#39;ex&#233;cution d&#39;un workflow &#224; l&#39;aide du suivi | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# D&#233;termination de la dur&#233;e d&#39;ex&#233;cution d&#39;un workflow &#224; l&#39;aide du suivi
Cette rubrique montre comment déterminer le temps nécessaire à l'exécution avec succès d'un workflow auto\-hébergé à l'aide du suivi de workflow.  
  
### Pour déterminer la durée d'exécution d'une application de workflow à l'aide du suivi  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].Sélectionnez **Fichier**, **Nouveau**, puis **Projet**.Sous **C\#**, sélectionnez le nœud **Workflow**.Sélectionnez **Application console de workflow** dans la liste des modèles.Nommez le nouveau projet `WorkflowDurationTracing` et cliquez sur **OK**.  
  
2.  Ouvrez le fichier Workflow1.xaml.Faites glisser une activité <xref:System.Activities.Statements.Delay> sur l'aire du concepteur.Affectez la valeur 00:00:10 \(dix secondes\) à la propriété Duration de l'activité.  
  
3.  Ouvrez l'Observateur d'événements en cliquant sur **Démarrer**, puis sur **Exécuter** et en entrant `eventvwr.exe`.  
  
4.  Si vous n'avez pas activé le suivi de workflow, développez **Journaux des applications et des services**, **Microsoft**, **Windows** et **Serveur d'applications\-Applications**.Sélectionnez **Afficher** et **Afficher les journaux d'analyse et de débogage**.Cliquez avec le bouton droit sur **Déboguer** et sélectionnez **Activer le journal**.Laissez l'Observateur d'événements ouvert afin que les traces soient visibles après l'exécution du workflow.  
  
5.  Exécutez l'application de workflow en appuyant sur Ctrl\+Maj\+B.  
  
6.  Dans l'Observateur d'événements, recherchez un événement récent portant l'ID 1009 et un message semblable au suivant.Notez l'heure à laquelle le message a été enregistré.  
  
 **Activité parente '', DisplayName : '', InstanceId : '' activité enfant planifiée 'WorkflowDurationTracking.Workflow1', DisplayName : 'Workflow1', InstanceId : '1'.**  
  
7.  Recherchez un autre événement récent portant l'ID 1001 et un message semblable au suivant.Soustrayez l'heure du message précédent de la valeur enregistrée dans ce message pour déterminer la durée d'exécution du workflow, qui doit être d'environ dix secondes.  
  
 **ID WorkflowInstance : '1bbac57b\-3322\-498e\-9e27\-8833fda3a5bf' s'est terminé dans l'état Closed.**  
  
## Voir aussi  
 [Suivi de workflow](../../../docs/framework/windows-workflow-foundation//workflow-tracing.md)   
 [Analyse Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201273)   
 [Analyse d'applications avec AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)