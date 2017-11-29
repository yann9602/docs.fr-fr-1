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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0c2c5d54050216c91a318a407341c4ffb9cb687
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
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
