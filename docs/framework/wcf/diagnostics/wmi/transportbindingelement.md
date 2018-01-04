---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 062b45eb5d627903142ca1a5fd4db6df0855384b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe TransportBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe TransportBindingElement a les propriétés suivantes :  
  
### <a name="manualaddressing"></a>ManualAddressing  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si l'utilisateur souhaite prendre le contrôle de l'adressage des messages.  
  
### <a name="maxbufferpoolsize"></a>MaxBufferPoolSize  
 Type de données : sint64  
  
 Type d'accès : lecture seule  
  
 Taille maximale du pool de mémoires tampons pour la liaison.  
  
### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize  
 Type de données : sint64  
  
 Type d'accès : lecture seule  
  
 Taille maximale d'un message traité par cette liaison.  
  
### <a name="scheme"></a>Scheme  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Schéma d'URI pour le transport.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
