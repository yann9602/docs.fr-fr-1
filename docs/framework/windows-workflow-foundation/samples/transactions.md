---
title: Transactions2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79970ad1220e3aab393a18cf52f94487702f37d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transactions"></a>Transactions
Cette section contient des exemples qui illustrent des transactions de workflow dans [!INCLUDE[wf](../../../../includes/wf-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Bases de TransactionScope](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 Est composé de quatre scénarios qui montrent comment imbriquer des instances <xref:System.Activities.Statements.TransactionScope>.  
  
 [Utilisation de TransactedReceiveScope](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 Montre comment passer une transaction d'un client à un serveur à l'aide de <xref:System.Activities.Statements.TransactionScope> pour créer une nouvelle transaction sur le client et un <xref:System.ServiceModel.Activities.TransactedReceiveScope> pour recevoir un message avec une transaction passée et étendre la durée de vie de la transaction sur le serveur.  
  
 [Imbrication de TransactionScope dans un service](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 Est composé de deux scénarios qui montrent comment gérer des instances d'activité <xref:System.Activities.Statements.TransactionScope> dans un service.
