---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f90ba7a245b36b24c190304f34a4481d1abda121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
Le service du protocole WS-AT a échoué l’enrôlement sur une transaction en utilisant le contexte de coordination fourni.  
  
## <a name="description"></a>Description  
 Suivi lorsque MSDTC ne peut pas enrôler sur une transaction pour un protocole 2PC donné.  Cela peut être dû au fait que la transaction n'existe plus, que l'enrôlement n'est plus autorisé, ou qu'un trop grand nombre d'enrôlements sont déjà présents.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.  
  
## <a name="see-also"></a>Voir aussi  
 [Le suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour dépanner votre Application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
