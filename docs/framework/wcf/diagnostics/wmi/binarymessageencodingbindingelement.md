---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe BinaryMessageEncodingBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe BinaryMessageEncodingBindingElement a les propriétés suivantes.  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.  
  
## <a name="maxsessionsize"></a>MaxSessionSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Valeur qui spécifie la taille, en octets, de la mémoire tampon utilisée pour l'encodage.  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 Type de données : XmlDictionaryReaderQuotas  
  
 Type d'accès : lecture seule  
  
 Quotas des lecteurs.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
