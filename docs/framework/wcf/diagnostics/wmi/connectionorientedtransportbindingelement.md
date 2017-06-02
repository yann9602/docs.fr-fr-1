---
title: "ConnectionOrientedTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## Syntaxe  
  
```  
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## Méthodes  
 La classe ConnectionOrientedTransportBindingElement ne définit pas de méthodes.  
  
## Propriétés  
 La classe ConnectionOrientedTransportBindingElement a les propriétés suivantes :  
  
### ChannelInitializationTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Le timespan qui spécifie le délai d'initialisation du canal avant expiration.  
  
### ConnectionBufferSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Taille de la mémoire tampon utilisée pour transmettre une portion du message sérialisé sur le câble du client ou du service.  
  
### HostNameComparisonMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.  
  
### MaxBufferSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Taille maximale autorisée de la mémoire tampon.  
  
### MaxOutputDelay  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Durée maximale pendant laquelle une portion d'un message ou un message complet peut rester en mémoire tampon avant d'être expédié.  
  
### MaxPendingAccepts  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de threads d'acceptation asynchrones en attente qui sont disponibles pour traiter des connexions entrantes sur le service.  
  
### MaxPendingConnections  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de connexions en attente.  
  
### TransferMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu par le transport orienté connexion.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>