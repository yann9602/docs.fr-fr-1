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
ms.workload: dotnet
ms.openlocfilehash: 4f13a39c251afd55dbb1f0d2dde4fc66fe38d30a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-exceptions"></a>Exceptions de transactions
Cette rubrique répertorie toutes les exceptions générées par la transaction [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Les informations de stratégie qui sont importées à partir des métadonnées spécifient des valeurs différentes pour TransactionProtocol au sein des opérations. Un seul TransactionProtocol est pris en charge pour chaque point de terminaison.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete ne peut pas avoir la valeur false à moins que la valeur InstanceContextMode du service soit PerSession. Une erreur a été détectée sur l'implémentation de l'opération et du contrat spécifiés.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete peut être appelé dans une opération uniquement lorsque TransactionAutoComplete à la valeur false et TransactionScopeRequired la valeur true. Ce scénario n’est pas valide et la transaction en cours est terminée.|  
|TransactionFlowRequiredIssuedTokens|Pour transmettre une transaction, la transmission des jetons émis doit également être prise en charge.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|La version de Trust configurée ne prend pas en charge les jetons émis. Utilisez WSTrustFeb2005 ou une version ultérieure.|
