---
title: "LocalServiceSecuritySettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## Syntaxe  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## Méthodes  
 La classe LocalServiceSecuritySettings ne définit pas de méthode.  
  
## Propriétés  
 La classe LocalServiceSecuritySettings a les propriétés suivantes :  
  
### DetectReplays  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si les attaques par relecture contre le canal sont détectées et traitées automatiquement.  
  
### InactivityTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de sessions de sécurité en attente que le service prend en charge.  
  
### IssuedCookieLifetime  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 TimeSpan qui spécifie la durée de vie de tous les nouveaux cookies de sécurité.  
  
### MaxCachedCookies  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de cookies qui peuvent être mis en cache.  
  
### MaxClockSkew  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 TimeSpan qui spécifie la différence de temps maximale entre les horloges système des deux parties communicantes.  
  
### MaxPendingSessions  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de connexions en attente sur le service.  
  
### MaxStatefulNegotiations  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre de négociations de sécurité qui peuvent être actives simultanément.  
  
### NegotiationTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 TimeSpan qui spécifie la durée maximale de la phase de négociation de sécurité entre le serveur et le client.  
  
### ReconnectTransportOnFailure  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si des connexions utilisant la messagerie WS\-Reliable tentent une reconnexion après des incidents de transport.  
  
### ReplayCacheSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre de pointeurs en cache utilisés pour la détection de relecture.  
  
### ReplayWindow  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 TimeSpan qui spécifie la durée de validité des pointeurs de messages individuels.  
  
### SessionKeyRenewalInterval  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 TimeSpan qui spécifie le délai d'attente au terme duquel l'initiateur renouvelle la clé de la session de sécurité.  
  
### SessionKeyRolloverInterval  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 TimeSpan qui spécifie la période de validité d'une clé de session précédente sur les messages entrants pendant un renouvellement de clé.  
  
### TimestampValidityDuration  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 TimeSpan qui spécifie la durée de validité d'un horodatage.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>