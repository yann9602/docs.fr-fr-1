---
title: Service
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 027366e7bf7abd285ef65da2040514b4b9908213
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="service"></a>Service
Service  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe Service ne définit aucune méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe Service a les propriétés suivantes :  
  
### <a name="baseaddresses"></a>BaseAddresses  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Les adresses de base utilisées par le service.  
  
### <a name="behaviors"></a>Comportements  
 Type de données : tableau de comportements  
  
 Type d'accès : lecture seule  
  
 Les comportements associés à ce service.  
  
### <a name="configurationname"></a>ConfigurationName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Le nom d'instance de l'instance des compteurs de performances du service.  
  
### <a name="distinguishedname"></a>DistinguishedName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom du service à cette adresse.  
  
### <a name="extensions"></a>Extensions  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Les contextes d'instance pour les extensions de l'instance de service.  
  
### <a name="metadata"></a>Métadonnées  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Les paramètres de métadonnées du service.  
  
### <a name="name"></a>Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Le nom unique de ce service.  
  
### <a name="namespace"></a>Espace de noms  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 L'espace de noms du service.  
  
### <a name="opened"></a>Opened  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 L'heure à laquelle le service a été ouvert.  
  
### <a name="outgoingchannels"></a>OutgoingChannels  
 Type de données : tableau de canaux  
  
 Type d'accès : lecture seule  
  
 Les canaux qui sortent de l'instance de service.  
  
### <a name="processid"></a>ProcessId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 L'ID de processus du processus qui héberge le service.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|
