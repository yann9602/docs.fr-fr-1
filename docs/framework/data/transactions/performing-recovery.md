---
title: "Exécution de la récupération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a215a7f516c2a3f0173b2ebfbd1c52911dee654
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="performing-recovery"></a>Exécution de la récupération
Un gestionnaire de ressources facilite la résolution d’inscriptions durables à une transaction en réinscrivant le participant à la transaction après défaillance de la ressource.  
  
## <a name="the-recovery-process"></a>Processus de récupération  
 Pour procéder à l'inscription durable d'une ressource (décrite par implémentation de l'interface <xref:System.Transactions.IEnlistmentNotification>) pouvant être utilisée pour une éventuelle récupération, appelez la méthode <xref:System.Transactions.Transaction.EnlistDurable%2A>. Vous devez également communiquer à la méthode <xref:System.Transactions.Transaction.EnlistDurable%2A> l'identificateur d'un gestionnaire de ressources (un <xref:System.Guid>) utilisé pour identifier systématiquement le participant à la transaction en cas de défaillance de la ressource. Pour cette raison, le <xref:System.Guid> qui est fournie pour l’inscription initiale appel doit être identique à la *resourceManagerIdentifier* paramètre dans le <xref:System.Transactions.TransactionManager.Reenlist%2A> appeler lors de la récupération. sous peine de lever une exception <xref:System.Transactions.TransactionException>. Pour plus d’informations sur les inscriptions durables, consultez [l’inscription des ressources en tant que Participants dans une Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) .  
  
 Au cours de la phase de préparation (phase 1) du protocole 2PC, lorsque l'implémentation du gestionnaire de ressources durables reçoit la notification <xref:System.Transactions.IEnlistmentNotification.Prepare%2A>, elle doit consigner son enregistrement de préparation. L'enregistrement doit contenir toutes les informations nécessaires pour terminer la transaction en cours de validation. L’enregistrement de préparation ultérieurement sont accessibles lors de la récupération en récupérant le <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> propriété de la *preparingEnlistment* rappel. Il n'est pas nécessaire d'effectuer la journalisation de l'enregistrement au sein de la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> puisque le gestionnaire de ressources peut le faire au niveau d'un thread de travail.  
  
 Le processus de récupération se divise en deux étapes :  
  
### <a name="step-1---reenlist"></a>Étape 1 : Réinscription  
 Le gestionnaire de ressources examine l'enregistrement d'informations de préparation de chaque inscription incertaine. Cette opération se traduit par l'examen de la propriété <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> du rappel <xref:System.Transactions.PreparingEnlistment>, passée au gestionnaire de ressources dans la notification <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> au cours de la phase 1.  
  
 Pour chaque inscription examinée, il appelle <xref:System.Transactions.TransactionManager.Reenlist%2A> sur le gestionnaire de transactions. Cette méthode passe le <xref:System.Guid> unique qui permet d'identifier le gestionnaire de ressources, ainsi que les informations d'inscription dans un tableau d'octets. Un nouvel objet <xref:System.Transactions.Enlistment> est retourné. Si la réinscription échoue avec une exception, le gestionnaire de ressources doit retenter ultérieurement.  
  
 N'appelez la méthode <xref:System.Transactions.TransactionManager.Reenlist%2A> que lors du redémarrage d'un gestionnaire de ressources après défaillance. En outre, vous ne devez réinscrire que des transactions non résolues enregistrées par un gestionnaire de ressources au cours de la phase de préparation initiale d'une validation en deux phases. Toute tentative pour appeler cette méthode à une période incorrecte peut entraîner des résultats erronés.  
  
 Lorsqu'un participant est réinscrit à l'aide de cette méthode, les méthodes de phase 2 de <xref:System.Transactions.IEnlistmentNotification> qui correspondent au résultat de la transaction (soit <xref:System.Transactions.IEnlistmentNotification.Commit%2A>, <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> ou <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A>) sont appelées si nécessaire.  
  
### <a name="step-2---completing-the-recovery"></a>Étape 2 : Fin de la récupération  
 Une fois toutes les réinscriptions effectuées, le gestionnaire des ressources appelle la méthode <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>. Cette méthode termine la récupération et informe le gestionnaire de transactions que le gestionnaire de ressources ne présente plus de transactions incertaines. Cela permet d'éviter que le gestionnaire de ressources ne rappelle la méthode <xref:System.Transactions.TransactionManager.Reenlist%2A>.  
  
 Il n'est pas nécessaire que le gestionnaire de ressources ait résolu toutes les transactions incertaines avant de procéder aux inscriptions à de nouvelles transactions. La première étape peut être effectuée à tout moment après que le Gestionnaire de ressources établit une relation avec le Gestionnaire de transactions, mais après <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> a été appelée (étape 2) ; étape 1 ne peut pas être exécutée à nouveau. L'étape 2 peut être répétée plusieurs fois sans affecter le résultat des transactions.
