---
title: "ChannelPoolSettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ChannelPoolSettings
ChannelPoolSettings  
  
## Syntaxe  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## Méthodes  
 La classe ChannelPoolSettings ne définit pas de méthode.  
  
## Propriétés  
 La classe ChannelPoolSettings a les propriétés suivantes :  
  
### IdleTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.  
  
### LeaseTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Période maximale d'exécution d'une opération de bail avant expiration du délai d'attente.  
  
### MaxOutboundChannelsPerEndpoint  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de canaux sortants pour chaque point de terminaison.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>