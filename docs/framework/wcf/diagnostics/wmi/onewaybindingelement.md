---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abaacfb6541d41019a8d0cd6df53913c6b7911f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe OneWayBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe OneWayBindingElement a les propriétés suivantes :  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 Type de données : ChannelPoolSettings  
  
 Type d'accès : lecture seule  
  
 Paramètres du pool de canaux.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de canaux acceptés.  
  
### <a name="packetroutable"></a>PacketRoutable  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si le paquet peut être routé.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
