---
title: "Transactions | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
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
---
# Transactions
Cette section contient des exemples qui illustrent des transactions de workflow dans [!INCLUDE[wf](../../../../includes/wf-md.md)].  
  
## Dans cette section  
 [Bases de TransactionScope](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 Est composé de quatre scénarios qui montrent comment imbriquer des instances <xref:System.Activities.Statements.TransactionScope>.  
  
 [Utilisation de TransactedReceiveScope](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 Montre comment passer une transaction d'un client à un serveur à l'aide de <xref:System.Activities.Statements.TransactionScope> pour créer une nouvelle transaction sur le client et un <xref:System.ServiceModel.Activities.TransactedReceiveScope> pour recevoir un message avec une transaction passée et étendre la durée de vie de la transaction sur le serveur.  
  
 [Imbrication de TransactionScope dans un service](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 Est composé de deux scénarios qui montrent comment gérer des instances d'activité <xref:System.Activities.Statements.TransactionScope> dans un service.