---
title: "AppDomainInfo | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# AppDomainInfo
Informations du domaine d'application  
  
## Syntaxe  
  
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
  
## Méthodes  
 La classe AppDomainInfo ne définit pas de méthode.  
  
## Propriétés  
 La classe AppDomainInfo a les propriétés suivantes :  
  
### AppDomainId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 ID de l'appdomain.  
  
### IsDefault  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si l'appdomain est l'appdomain par défaut.  
  
### LogMalformedMessages  
 Type de données : booléen  
  
 Type d'accès : lecture\/écriture  
  
 Valeur qui spécifie si les messages incorrects sont enregistrés.  
  
### LogMessagesAtServiceLevel  
 Type de données : booléen  
  
 Type d'accès : lecture\/écriture  
  
 Valeur qui spécifie si les messages sont suivis au niveau du service \(avant les transformations associées au chiffrement et au transport\).  
  
### LogMessagesAtTransportLevel  
 Type de données : booléen  
  
 Type d'accès : lecture\/écriture  
  
 Valeur qui spécifie si les messages sont suivis au niveau du transport.  
  
### MessageLoggingTraceListeners  
 Type de données : tableau TraceListener  
  
 Type d'accès : lecture seule  
  
 Écouteurs de suivi de la collection qui écoutent la source de suivi System.Wmi.MessageLogging.  
  
### Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom de l'appdomain.  
  
### PerformanceCounters  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Portée de compteurs de performance actifs dans l'appdomain.  
  
### ProcessId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 ID de processus.  
  
### ServiceConfigPath  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Chemin d'accès à la configuration du service.  
  
### TraceLevel  
 Type de données : chaîne  
  
 Type d'accès : lecture\/écriture  
  
 Niveau de suivi de la source de suivi System.Wmi.  
  
### ServiceModelTraceListeners  
 Type de données : tableau TraceListener  
  
 Type d'accès : lecture seule  
  
 Collection d'écouteurs de la source de suivi System.ServiceModel.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|