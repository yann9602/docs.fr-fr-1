---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5038d093333eca9ca191c3ecae4cfa889d723276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings
TcpConnectionPoolSettings  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe TcpConnectionPoolSettings ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe TcpConnectionPoolSettings a les propriétés suivantes :  
  
### <a name="groupname"></a>GroupName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom de groupe du pool de connexions utilisé par l'élément de liaison.  
  
### <a name="idletimeout"></a>IdleTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Période maximale d'exécution de l'opération de bail avant expiration du délai d'attente.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de connexions sortantes pour chaque point de terminaison.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
