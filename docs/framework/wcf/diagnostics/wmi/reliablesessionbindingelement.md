---
title: "ReliableSessionBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## Syntaxe  
  
```  
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## Méthodes  
 La classe ReliableSessionBindingElement ne définit pas de méthodes.  
  
## Propriétés  
 La classe ReliableSessionBindingElement a les propriétés suivantes :  
  
### AcknowledgementInterval  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Intervalle d'attente d'une destination avant l'envoi d'un accusé de réception à la source de message sur les canaux fiables créés par la fabrique.  
  
### FlowControlEnabled  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si le contrôle de flux est activé.  
  
### InactivityTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Spécifie la durée maximale pendant laquelle le canal va laisser l'autre partie communicante ne pas envoyer des messages avant de provoquer une erreur sur le canal.  
  
### MaxPendingChannels  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de canaux qui peuvent attendre d'être acceptés sur l'écouteur.  
  
### MaxRetryCount  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de tentatives qu'un canal fiable peut effectuer pour retransmettre un message dont il n'a pas reçu d'accusé de réception, en appelant `Send` sur son canal sous\-jacent.  
  
### MaxTransferWindowSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Taille de fenêtre de transfert maximale pour la session fiable.  
  
### Ordered  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si l'arrivée de messages est garantie dans leur ordre d'envoi.  
  
### ReliableMessagingVersion  
 Type de données : entier  
  
 Type d'accès : lecture seule  
  
 Entier qui spécifie la version du protocole WS\-ReliableMessaging utilisée dans la session fiable.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>