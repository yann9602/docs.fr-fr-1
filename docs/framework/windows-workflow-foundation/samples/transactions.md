---
title: "Transactions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Transactions
Cette section contient des exemples qui illustrent des scénarios qui utilisent des transactions de workflow dans [!INCLUDE[wf](../../../../includes/wf-md.md)].  
  
## Dans cette section  
 [Exécuter un workflow dans un TransactionScope impératif](../../../../docs/framework/windows-workflow-foundation/samples/execute-a-workflow-in-an-imperative-transactionscope.md)  
 Montre comment exécuter un workflow à l'aide de <xref:System.Activities.WorkflowInvoker> sous un <xref:System.Transactions.Transaction> à partir de code C\# impératif.  
  
 [Étendue du convoi des transactions](../../../../docs/framework/windows-workflow-foundation/samples/transaction-convoy-scope.md)  
 Montre comment créer un modèle d'activité de messagerie de convoi parallèle conjointement avec un <xref:System.ServiceModel.Activities.TransactedReceiveScope> pour modéliser un protocole où un certain nombre d'opérations peuvent se produire dans n'importe quel ordre dans le cadre de la même transaction.  
  
 [Restauration de transaction](../../../../docs/framework/windows-workflow-foundation/samples/transaction-rollback.md)  
 Montre comment créer un <xref:System.Activities.NativeActivity> personnalisé qui accède au <xref:System.Activities.RuntimeTransactionHandle> ambiant pour obtenir la transaction ambiante et la restaurer explicitement.  
  
 [Étendue de transaction de suppression](../../../../docs/framework/windows-workflow-foundation/samples/suppress-transaction-scope.md)  
 Montre comment créer une activité `SuppressTransactionScope` personnalisée pour supprimer la transaction runtime ambiante, si elle existe.  
  
 [Files d'attente avec transaction](../../../../docs/framework/windows-workflow-foundation/samples/transacted-queues.md)  
 Montre comment intégrer des files d'attente et des transactions dans [!INCLUDE[wf1](../../../../includes/wf1-md.md)] pour créer des services fiables et évolutifs.