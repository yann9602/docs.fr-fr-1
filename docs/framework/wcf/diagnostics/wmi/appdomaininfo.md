---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76fee9673514287dd120a215fc843e4d995e68c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="appdomaininfo"></a>AppDomainInfo
Informations du domaine d'application  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe AppDomainInfo ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe AppDomainInfo a les propriétés suivantes :  
  
### <a name="appdomainid"></a>AppDomainId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 ID de l'appdomain.  
  
### <a name="isdefault"></a>IsDefault  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si l'appdomain est l'appdomain par défaut.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Type de données : booléen  
  
 Type d'accès : lecture/écriture  
  
 Valeur qui spécifie si les messages incorrects sont enregistrés.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Type de données : booléen  
  
 Type d'accès : lecture/écriture  
  
 Valeur qui spécifie si les messages sont suivis au niveau du service (avant les transformations associées au chiffrement et au transport).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 Type de données : booléen  
  
 Type d'accès : lecture/écriture  
  
 Valeur qui spécifie si les messages sont suivis au niveau du transport.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Type de données : tableau TraceListener  
  
 Type d'accès : lecture seule  
  
 Écouteurs de suivi de la collection qui écoutent la source de suivi System.Wmi.MessageLogging.  
  
### <a name="name"></a>Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom de l'appdomain.  
  
### <a name="performancecounters"></a>PerformanceCounters  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Portée de compteurs de performance actifs dans l'appdomain.  
  
### <a name="processid"></a>ProcessId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 ID de processus.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Chemin d'accès à la configuration du service.  
  
### <a name="tracelevel"></a>TraceLevel  
 Type de données : chaîne  
  
 Type d'accès : lecture/écriture  
  
 Niveau de suivi de la source de suivi System.Wmi.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Type de données : tableau TraceListener  
  
 Type d'accès : lecture seule  
  
 Collection d'écouteurs de la source de suivi System.ServiceModel.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|
