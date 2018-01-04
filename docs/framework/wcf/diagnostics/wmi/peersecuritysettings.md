---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48a9cc5a7a05b47a5589d1bf9a730184fb7f0543
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe PeerSecuritySettings ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe PeerSecuritySettings a les propriétés suivantes :  
  
### <a name="mode"></a>Mode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Utilisation ou non d’une sécurité au niveau du message et au niveau du transport par un point de terminaison configuré avec la liaison.  
  
### <a name="transport"></a>Transport  
 Type de données : PeerTransportSecuritySettings  
  
 Type d'accès : lecture seule  
  
 Paramètres de sécurité du transport.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.PeerSecuritySettings>
