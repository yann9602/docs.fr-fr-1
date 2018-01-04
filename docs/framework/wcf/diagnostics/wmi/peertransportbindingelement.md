---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25893b1f3cf6cf20ae674bade5090a70c5f381a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe PeerTransportBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe PeerTransportBindingElement a les propriétés suivantes :  
  
### <a name="listenipaddress"></a>ListenIPAddress  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Adresse IP sur laquelle le nœud homologue écoute les messages.  
  
### <a name="port"></a>Port  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Port d’interface de réseau sur lequel la liaison traite les messages de canaux homologues.  
  
### <a name="security"></a>Sécurité  
 Type de données : PeerSecuritySettings  
  
 Type d'accès : lecture seule  
  
 Paramètres de sécurité de transport de l'homologue.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
