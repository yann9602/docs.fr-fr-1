---
title: "&lt;udpTransportSettings&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;udpTransportSettings&gt;
Cet élément de configuration expose les paramètres de transport UDP de [\<UdpDiscoveryEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <udpDiscoveryEndpoint>   
          <standardEndpoint>  
               <updTransportSettings>  
                  duplicateMessageHistoryLength=”Integer”  
                  maxBufferPoolSize=”Integer”   
                  maxMulticastRetransmitCount=”Integer”  
                  maxPendingMessageCount=”Integer”  
                  maxReceivedMessageSize=”Integer”  
                  maxUnicastRetransmitCount=”Integer”  
                  multicastInterfaceId=”String”  
                  socketReceiveBufferSize=”Integer”  
                  timeToLive=”Integer” />   
          </standardEndpoint>  
       </udpDiscoveryEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|duplicateMessageHistoryLength|Entier qui spécifie le nombre maximal de hachages de messages utilisés par le transport pour l'identification des messages dupliqués.  La détection des doublons est effectuée au niveau de TransportManager.  Si cette propriété a la valeur 0, la détection des doublons est désactivée.<br /><br /> Cet attribut permet aux administrateurs système ou aux développeurs de désactiver les algorithmes de détection des messages dupliqués.  Cela peut s'avérer utile si vous souhaitez implémenter votre propre algorithme de détection de doublons.<br /><br /> La valeur par défaut est 4112.|  
|maxBufferPoolSize|Entier qui spécifie la taille maximale des pools de mémoires tampons utilisés par le transport.|  
|maxMulticastRetransmitCount|Entier qui spécifie le nombre maximal de retransmissions du message \(en plus du premier envoi\).<br /><br /> La valeur par défaut est 2.|  
|maxPendingMessageCount|Entier qui spécifie le nombre maximal de messages reçus qui n'ont pas encore été supprimés dans InputQueue pour une instance de canal individuelle.  Si InputQueue a atteint sa limite du nombre de messages en attente, le message est supprimé.<br /><br /> La valeur par défaut est 32.|  
|maxReceivedMessageSize|Entier qui spécifie la taille maximale d'un message pouvant être traité par la liaison.<br /><br /> La valeur par défaut est 65507.|  
|maxUnicastRetransmitCount|Entier qui spécifie le nombre maximal de retransmissions du message \(en plus du premier envoi\).  Si le message est envoyé à une adresse unicast et qu'un message de réponse est reçu avec un en\-tête RelatesTo correspondant, la retransmission peut se terminer de manière précoce \(avant le nombre de retransmissions configuré\).<br /><br /> La valeur par défaut est 1.|  
|multicastInterfaceId|Chaîne qui identifie de manière unique la carte réseau à utiliser lors de l'envoi et de la réception du trafic multidiffusion sur des ordinateurs multirésidents.  Au moment de l'exécution, le transport utilise cette valeur d'attribut pour rechercher l'index d'interface, qui permet ensuite de définir les options de socket `IPV6_MULTICAST_IF` et `IP_MULTICAST_IF`.  Le même index d'interface est utilisé pour rejoindre un groupe de multidiffusion \(le cas échéant\).<br /><br /> La valeur par défaut est `null`.|  
|socketReceiveBufferSize|Entier qui spécifie la taille du tampon de réception pour le socket WinSock sous\-jacent.<br /><br /> Tout utilisateur d'un canal de réception peut se servir de cet attribut sur la liaison pour contrôler le comportement du système lorsqu'il reçoit des données.  Par exemple, si une application consomme des messages WCF entrants au seuil maximal, l'utilisation d'une valeur supérieure pour cet attribut permettrait aux messages de s'empiler dans la mémoire tampon Winsock en attendant que l'application puisse les traiter.  L'utilisation d'une valeur inférieure dans la même situation entraînerait la suppression des messages. Cet attribut expose l'option de socket Winsock `SO_RCVBUF` sous\-jacente. Cette valeur d'attribut doit avoir au moins la taille de `maxReceivedMessageSize`.  Si sa valeur est inférieure à `maxReceivedMessageSize` une exception runtime se produit.<br /><br /> La valeur par défaut est 65536.|  
|timeToLive|Entier qui spécifie le nombre de tronçons de segments réseau pouvant être traversés par un paquet multidiffusion.  Cette propriété expose la fonctionnalité associée aux options de socket `IP_TTL` et `IP_MULTICAST_TTL`.<br /><br /> La valeur par défaut est 1.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<UdpDiscoveryEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Point de terminaison standard qui a un contrat de découverte fixe et une liaison de transport UDP.|  
  
## Voir aussi  
 <xref:System.Servicemodel.Discovery.UdpTransportSettings>