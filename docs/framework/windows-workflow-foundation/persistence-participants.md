---
title: Participants de persistance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a19099ea928e8867dd8206b8add0f1146496d052
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="persistence-participants"></a>Participants de persistance
Un participant de persistance peut participer à une opération de persistance (enregistrement ou chargement) déclenchée par un hôte d'application. Le [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] est fourni avec deux classes abstraites, **PersistenceParticipant** et **PersistenceIOParticipant**, que vous pouvez utiliser pour créer un participant de persistance. Un participant de persistance dérive de l'une de ces classes, implémente les méthodes qui l'intéressent, puis ajoute une instance de la classe à la collection <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> sur le <xref:System.ServiceModel.Activities.WorkflowServiceHost>. L'hôte d'application peut rechercher de telles extensions de workflow lorsqu'il rend une instance de workflow persistante et appeler les méthodes appropriées sur les participants de persistance aux moments opportuns.  
  
 La liste suivante décrit les tâches effectuées par le sous-système de persistance lors des différentes étapes de l'opération de persistance (enregistrement). Les participants de persistance sont utilisés durant les troisième et quatrième étapes. Si le participant est un participant d'E/S (un participant de persistance qui participe également aux opérations d'E/S), il est également utilisé lors de la sixième étape.  
  
1.  Recueille les valeurs intégrées, notamment l'état du workflow, les signets, les variables mappées et l'horodatage.  
  
2.  Recueille tous les participants de persistance ajoutés à la collection d'extensions associée à l'instance de workflow.  
  
3.  Appelle la méthode <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> implémentée par tous les participants de persistance.  
  
4.  Appelle la méthode <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> implémentée par tous les participants de persistance.  
  
5.  Rend le workflow persistant ou l'enregistre dans le magasin de persistances.  
  
6.  Appelle la méthode <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> sur tous les participants d'E/S de persistance. Si le participant n'est pas un participant d'E/S, cette tâche est ignorée. Si l'épisode de persistance est transactionnel, la transaction est fournie dans la propriété Transaction.Current.  
  
7.  Attend que tous les participants de persistance soient terminés. Si tous les participants réussissent à rendre les données d'instance persistantes, valide la transaction.  
  
 Un participant de persistance dérive le **PersistenceParticipant** de classe et peut implémenter la **CollectValues** et **MapValues** méthodes. Un participant d’e/s de persistance dérive le **PersistenceIOParticipant** de classe et peut implémenter la **BeginOnSave** méthode en plus d’implémenter la **CollectValues**et **MapValues** méthodes.  
  
 Chaque étape est terminée avant que l'étape suivante ne commence. Par exemple, les valeurs sont recueillies à partir de **tous les** participants de persistance de la première étape. Toutes les valeurs recueillies dans la première étape sont ensuite fournies à tous les participants de persistance lors de la deuxième étape, en vue de leur mappage. Puis toutes les valeurs recueillies et mappées lors des première et deuxième étapes sont fournies au fournisseur de persistance durant la troisième étape, et ainsi de suite.  
  
 La liste suivante décrit les tâches effectuées par le sous-système de persistance lors des différentes étapes de l'opération de chargement. Les participants de persistance sont utilisés lors de la quatrième étape. Les participants d'E/S de persistance (les participants de persistance qui participent également aux opérations d'E/S) sont également utilisés lors de la troisième étape.  
  
1.  Recueille tous les participants de persistance ajoutés à la collection d'extensions associée à l'instance de workflow.  
  
2.  Charge le workflow à partir du magasin de persistances.  
  
3.  Appelle la méthode <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> sur toute les participants d'E/S de persistance et attend que tous les participants de persistance soient terminés. Si l'épisode de persistance est transactionnel, la transaction est fournie dans la propriété Transaction.Current.  
  
4.  Charge l'instance de workflow en mémoire selon les données récupérées dans le magasin de persistances.  
  
5.  Appelle la méthode <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> sur chaque participant de persistance.  
  
 Un participant de persistance dérive le **PersistenceParticipant** de classe et peut implémenter la **PublishValues** (méthode). Un participant d’e/s de persistance dérive le **PersistenceIOParticipant** de classe et peut implémenter la **BeginOnLoad** méthode en plus d’implémenter la **PublishValues**(méthode).  
  
 Lors du chargement d'une instance du workflow, le fournisseur de persistance crée un verrou sur cette instance. Cela empêche l'instance d'être chargée dans plusieurs hôtes dans un scénario multi-nœud. Si vous essayez de charger une instance de workflow qui a été verrouillée, vous verrez une exception semblable à la suivante : l’exception « System.ServiceModel.Persistence.InstanceLockException : Impossible de terminer l’opération demandée car le verrou pour l’instance ' 00000000-0000-0000-0000-type "000000000000" ' n’a pas pu être obtenu. ». Cette erreur se produit généralement lorsque l'une des conditions suivantes se vérifie :  
  
-   Dans un scénario multi-nœud l'instance est chargée par un autre hôte.  Il existe différentes manières de résoudre ces types de conflits : transférer le traitement au nœud qui possède le verrou et réessayer, ou forcer la charge ce qui empêche l'autre hôte d'enregistrer son travail.  
  
-   Dans un scénario à nœud unique et l'hôte est bloqué.  Lorsque l'hôte redémarre (recyclage de processus ou création d'une fabrique de fournisseur de persistance), le nouvel hôte tente de charger une instance qui est encore verrouillée par l'ancien hôte, car le verrou n'a pas encore expiré.  
  
-   Dans un scénario à nœud unique, l'instance en question a été abandonnée à un certain point et une instance de fournisseur de persistance est créée avec un autre ID d'hôte.  
  
 La valeur d'expiration du verrou est par défaut de cinq minutes, vous pouvez spécifier un délai d'attente différent en appelant <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Guide pratique pour créer un participant de persistance personnalisé](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Stocker l’extensibilité](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)
