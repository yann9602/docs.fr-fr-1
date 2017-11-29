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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43707f25a9ee1beb1ce7adac36a2c4a55cab6d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
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
