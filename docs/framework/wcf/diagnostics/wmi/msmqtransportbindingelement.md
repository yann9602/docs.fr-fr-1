---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 572a19723583a6bc717a71b3b46040148f29e1cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe MsmqTransportBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe MsmqTransportBindingElement a les propriétés suivantes :  
  
### <a name="maxpoolsize"></a>MaxPoolSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Taille maximale du pool contenant des objets de message MSMQ internes.  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur d'énumération qui indique le transport de canal de communication mis en file d'attente que cette liaison utilise.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Retourne une valeur Boolean qui indique si les adresses de file d'attente doivent être converties à l'aide d'Active Directory.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
