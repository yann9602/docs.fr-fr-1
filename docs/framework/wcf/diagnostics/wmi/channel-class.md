---
title: Channel, classe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 073f0a2a2731a08acd914a7dd85cb2b419d98128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="channel-class"></a>Channel, classe
Canal  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe Channel ne définit aucune méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe Channel possède les propriétés suivantes.  
  
### <a name="localaddress"></a>LocalAddress  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Point de terminaison local du canal.  
  
### <a name="ref"></a>ref  
 Type de données : point de terminaison  
  
 Type d'accès : lecture seule  
  
 Référence au point de terminaison auquel le canal se connecte.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Adresse distante associée au canal.  
  
### <a name="sessionid"></a>SessionId  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Id de session actuel, le cas échéant.  
  
### <a name="type"></a>Type  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Type du canal.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.ChannelBase>
