---
title: MsmqBindingElementBase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 009596ee8fd7218a07487183d932e91dad07797c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe MsmqBindingElementBase ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe MsmqBindingElementBase a les propriétés suivantes :  
  
### <a name="customdeadletterqueue"></a>CustomDeadLetterQueue  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 URI qui contient l'emplacement de la file d'attente de lettres mortes pour chaque application, dans laquelle les messages expirés ou dont le transfert ou la remise a échoué sont placés.  
  
### <a name="deadletterqueue"></a>DeadLetterQueue  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur d'énumération qui indique le type de la file d'attente de lettres mortes à utiliser.  
  
### <a name="durable"></a>Durable  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si les messages traités par cette liaison sont durables ou volatils.  
  
### <a name="exactlyonce"></a>ExactlyOnce  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui indique si les messages traités par cette liaison sont reçus exactement une fois.  
  
### <a name="maxretrycycles"></a>MaxRetryCycles  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de cycles de nouvelle tentative de livraison de messages à l'application de réception.  
  
### <a name="receiveerrorhandling"></a>ReceiveErrorHandling  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres de gestion de messages incohérents.  
  
### <a name="receiveretrycount"></a>ReceiveRetryCount  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de nouvelles tentatives immédiates sur un message qui est lu à partir de la file d'attente d'application.  
  
### <a name="retrycycledelay"></a>RetryCycleDelay  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique l'intervalle entre des cycles de nouvelle tentative de remise d'un message n'ayant pas pu être remis immédiatement.  
  
### <a name="timetolive"></a>TimeToLive  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Intervalle qui indique combien de temps les messages traités par cette liaison peuvent séjourner dans la file d'attente avant expiration.  
  
### <a name="usemsmqtracing"></a>UseMsmqTracing  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui indique si les messages traités par cette liaison doivent être suivis.  
  
### <a name="usesourcejournal"></a>UseSourceJournal  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui indique si les copies des messages traités par cette liaison doivent être stockées dans la file d'attente du journal source.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
