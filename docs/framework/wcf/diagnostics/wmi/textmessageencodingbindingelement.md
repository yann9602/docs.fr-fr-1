---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 966f1ae06f5d7e0dacb8b7d450463c75f783ef1f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="textmessageencodingbindingelement"></a>TextMessageEncodingBindingElement
TextMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe TextMessageEncodingBindingElement ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  
 La classe TextMessageEncodingBindingElement a les propriétés suivantes :  
  
### <a name="encoding"></a>Encodage  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.  
  
### <a name="readerquotas"></a>ReaderQuotas  
 Type de données : XmlDictionaryReaderQuotas  
  
 Type d'accès : lecture seule  
  
 Quotas des lecteurs.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
