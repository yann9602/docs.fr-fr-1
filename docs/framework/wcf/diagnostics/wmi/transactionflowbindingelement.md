---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b073efc47ccc1708bf4c58153b1001a21eee25f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe TransactionFlowBindingElement ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  
 La classe TransactionFlowBindingElement dispose des propriétés suivantes :  
  
### <a name="issuedtokens"></a>IssuedTokens  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Définit les exigences d’un en-tête de jetons de sécurité publié (IssuedTokens de WS-Trust).  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Protocole de transactions utilisé par le service pour transférer les transactions.  
  
### <a name="transactions"></a>Transactions  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si la transaction entrante est prise en charge.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
