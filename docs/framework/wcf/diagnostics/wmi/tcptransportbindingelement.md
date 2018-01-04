---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e230cbccee211fbda219000fbbd2cda5275776b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe TcpTransportBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe TcpTransportBindingElement a les propriétés suivantes :  
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  
 Type de données : TcpConnectionPoolSettings  
  
 Type d'accès : lecture seule  
  
 Paramètres de pool de connexions.  
  
### <a name="listenbacklog"></a>ListenBacklog  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de demandes de connexion en file d'attente pouvant être en attente.  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si le partage de port TCP est activé pour cette connexion.  
  
### <a name="teredoenabled"></a>TeredoEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si Teredo (technologie d'adressage de clients placés derrière des pare-feu) est activé.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
