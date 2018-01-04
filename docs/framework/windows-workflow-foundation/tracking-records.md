---
title: Enregistrements de suivi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c871f019179c091fc022be0bf03ad84fbe66dc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-records"></a>Enregistrements de suivi
L'exécution du flux de travail est instrumentée pour émettre des enregistrements de suivi pour suivre l'exécution d'une instance de workflow.  
  
## <a name="tracking-records"></a>Enregistrements de suivi  
 Le tableau suivant détaille les enregistrements de suivi que l'exécution de workflow émet.  
  
|Enregistrement de suivi|Description|  
|---------------------|-----------------|  
|Enregistrements du cycle de vie du flux de travail|Émis pendant différentes étapes du cycle de vie de l'instance de workflow. Par exemple, un enregistrement est émis lorsque le flux de travaille démarre ou se termine.|  
|Enregistrements du cycle de vie de l'activité|Détaille l'exécution de l'activité. Ces enregistrements indiquent l'état d'une activité de workflow, par exemple lorsqu'une activité est planifiée, lorsque l'activité se termine, ou lorsqu'une erreur se produit.|  
|Enregistrements de reprise de signet|Émis chaque fois qu'un signet au sein d'une instance de workflow est repris.|  
|Suivi personnalisé des enregistrements|Un auteur de workflow peut créer des enregistrements de suivi personnalisés et les émettre dans une activité personnalisée.|  
  
 Tous les enregistrements de suivi associés émis par le WF sont issus de la classe de base <xref:System.Activities.Tracking.TrackingRecord>, qui contient le jeu commun de données. Les enregistrements de suivi affichent le cycle de vie pour un workflow simple. Chaque enregistrement de suivi contient des détails à propos de l'événement de suivi associé, tel que  <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A> et des informations supplémentaires spécifiques au type d'enregistrement de suivi.  
  
 Les types suivants d'objets <xref:System.Activities.Tracking.TrackingRecord> sont émis par l'exécution du workflow :  
  
-   **WorkflowInstanceRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> décrit le cycle de vie de l’instance de flux de travail. Par exemple, un enregistrement est émis lorsque le workflow démarre ou se termine, et contient l'état de l'instance de workflow. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
-   **WorkflowInstanceAbortedRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est émis lorsqu’une instance de workflow est abandonnée. L'enregistrement contient la raison pour laquelle l'instance de workflow a échoué. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
-   **WorkflowInstanceUnhandledExceptionRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est émis si une exception se produit dans l’instance de workflow et n’est pas gérée par aucune activité. L'enregistrement contient les détails d'exception. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
-   **WorkflowInstanceSuspendedRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est émis chaque fois qu’une instance de workflow est suspendue. L'enregistrement contient la raison pour laquelle l'instance de workflow a été interrompue. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
-   **WorkflowInstanceTerminatedRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est émis chaque fois qu’une instance de workflow est arrêtée. L'enregistrement contient la raison pour laquelle l'instance de workflow a abouti. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
-   **ActivityStateRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est émis lorsqu’une activité dans un flux de travail s’exécute. Ces enregistrements indiquent l'état de l'activité dans l'instance de workflow. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
-   **ActivityScheduledRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est émis lorsqu’une activité planifie une activité enfant. Cet enregistrement contient des détails pour à la fois l'activité parent (planification de l'activité) et l'activité enfant planifiée. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
-   **FaultPropagationRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est émis pour chaque gestionnaire qui consulte l’enregistrement jusqu'à ce qu’elle est gérée. Il est utilisé pour dénoter le chemin d’accès qu’une erreur a pris dans l’instance de workflow. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
-   **CancelRequestedRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est émis chaque fois qu’une activité essaie d’annuler une activité enfant. Cet enregistrement contient des détails pour à la fois l'activité parent et l'activité enfant en cours d'annulation. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
-   **BookmarkResumptionRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> suit tout signet repris avec succès. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
-   **Événement CustomTrackingRecord** - ce <xref:System.Activities.Tracking.TrackingRecord> est créé et émis par un auteur de workflow dans une activité de flux de travail personnalisé. Les enregistrements de suivi personnalisés peuvent être remplis à l'aide des données utilisées pour remplir les enregistrements. Les détails de cet enregistrement se trouvent dans <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Par exemple, il pourrait y avoir une activité <xref:System.Activities.Statements.Sequence> simple qui contient une opération <xref:System.Activities.Statements.WriteLine> avec les enregistrements de suivi émis dans l'ordre suivant :  
  
1.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> indique que le flux de travail démarre.  
  
2.  <xref:System.Activities.Tracking.ActivityScheduledRecord> indique qu'une activité a été planifiée. Dans ce cas c'est une activité <xref:System.Activities.Statements.Sequence>.  
  
3.  <xref:System.Activities.Tracking.ActivityScheduledRecord> représente l'activité <xref:System.Activities.Statements.WriteLine>.  
  
4.  Il y a deux enregistrements <xref:System.Activities.Tracking.ActivityStateRecord> qui représentent les deux activités en cours.  
  
5.  <xref:System.Activities.Tracking.WorkflowInstanceRecord> indique que le flux de travail est terminé.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Analyse des Applications avec AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
