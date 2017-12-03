---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a4bbaca70954e5aa89dbcfd14723551de7848f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
Le service du protocole WS-AT a dépassé le délai spécifié lors de l'attente d'une réponse à un message de résultat provenant d'un participant volatil. Le résultat de la transaction peut s'avérer incertain si le participant retourne.  
  
## <a name="description"></a>Description  
 Suivi lorsqu'un participant volatil a décidé de valider ou d'abandonner mais n'a pas répondu à une demande de validation ou de restauration dans un délai donné.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Assurez-vous que tous les participants volatils sont en mesure de répondre dans le délai imparti. Le délai par défaut est de 180 secondes.  S'il est insuffisant, augmentez le délai du minuteur `VolatileOutcomeDelay` de WS-AT.  
  
## <a name="see-also"></a>Voir aussi  
 [Le suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour dépanner votre Application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
