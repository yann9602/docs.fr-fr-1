---
title: Exceptions de transactions
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5896f1f7e15fa7ed86f80bbd7c06ae77faded90
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-exceptions"></a>Exceptions de transactions
Cette rubrique répertorie toutes les exceptions générées par la transaction [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Les informations de stratégie qui sont importées à partir des métadonnées spécifient des valeurs différentes pour TransactionProtocol au sein des opérations. Un seul TransactionProtocol est pris en charge pour chaque point de terminaison.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete ne peut pas avoir la valeur false à moins que la valeur InstanceContextMode du service soit PerSession. Une erreur a été détectée sur l'implémentation de l'opération et du contrat spécifiés.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete peut être appelé dans une opération uniquement lorsque TransactionAutoComplete à la valeur false et TransactionScopeRequired la valeur true. Ce scénario n'est pas valide et la transaction en cours est terminée.|  
|TransactionFlowRequiredIssuedTokens|Pour transmettre une transaction, la transmission des jetons émis doit également être prise en charge.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|La version de Trust configurée ne prend pas en charge les jetons émis. Utilisez WSTrustFeb2005 ou une version ultérieure.|
