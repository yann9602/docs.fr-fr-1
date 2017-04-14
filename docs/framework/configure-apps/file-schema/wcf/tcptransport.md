---
title: "&lt;tcpTransport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;tcpTransport&gt;
Définit un transport TCP qui peut être utilisé par un canal pour transférer des messages pour une liaison personnalisée.  
  
## Syntaxe  
  
```  
  
<tcpTransport   
    listenBacklog="Integer"  
        portSharingEnabled="Boolean"  
    teredoEnabled="Boolean"  
    transferMode=”Buffered/Streamed”  
        <connectionPoolSettings  
          groupName=”String”  
        idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
        maxOutboundConnectionsPerEndpopint=”Integer” />  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|channelInitializationTimeout|Durée maximale de l'état d'initialisation du canal avant sa déconnexion \(en secondes\).  Cette propriété détermine la durée d'authentification d'une connexion TCP à l'aide du protocole .NET Message Framing.  Un client doit envoyer des données initiales avant que le serveur dispose de suffisamment d'informations pour exécuter l'authentification.  La valeur par défaut est 30 secondes.|  
|listenBacklog|Nombre maximal de demandes de connexion en file d'attente pouvant être en attente pour un service Web.  L'attribut `connectionLeaseTimeout` limite la durée d'attente d'un client pour être connecté avant de lever une exception de connexion.  Il s'agit d'une propriété de niveau socket qui contrôle le nombre maximal de demandes de connexion en file d'attente qui peuvent être en attente pour un service Web.  Lorsque ListenBacklog est trop faible, WCF arrête de recevoir des demandes et par conséquent supprime les nouvelles connexions jusqu'à ce que le serveur accepte certaines des connexions mises en file d'attente existantes. La valeur par défaut est 16 \* nombre de processeurs.|  
|portSharingEnabled|Valeur booléenne qui spécifie si le partage de port TCP est activé pour cette connexion.  Si la valeur affectée est `false`, chaque liaison utilisera son propre port exclusif.  La valeur par défaut est `false`.<br /><br /> Ce paramètre ne concerne que les services.  Les clients ne sont pas affectés.<br /><br /> L'utilisation de ce paramètre requiert l'activation du service de partage de port TCP de Windows Communication Foundation \(WCF\) en modifiant son type de démarrage sur Manuel ou Automatique|  
|teredoEnabled|Valeur booléenne qui spécifie si Teredo \(technologie d'adressage de clients placés derrière des pare\-feu\) est activé.  La valeur par défaut est `false`.<br /><br /> Cette propriété active Teredo pour le socket TCP sous\-jacent.  Pour plus d'informations, consultez [Vue d'ensemble de Teredo](http://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Cette propriété s'applique uniquement à [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] et [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)].  Pour Teredo, [!INCLUDE[wv](../../../../../includes/wv-md.md)] dispose d'une option de configuration à l'échelle de l'ordinateur. Cette propriété est donc ignorée lors de l'exécution de Vista.  Pour que Teredo fonctionne, la pile Microsoft IPv6 doit être installée et configurée correctement sur les ordinateurs clients et de service.  Pour plus d'informations sur la configuration de Teredo, consultez [Vue d'ensemble de Teredo](http://go.microsoft.com/fwlink/?LinkId=95339).  Pour plus d'informations, consultez [Centres de technologie Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=49888).|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Notes  
 Ce transport utilise des URI au format "net.tcp:\/\/nom\_hôte:port\/chemin".  Les autres composants URI sont facultatifs.  
  
 L'élément `tcpTransport` constitue le point de départ pour créer une liaison personnalisée qui implémente le protocole de transport TCP.  Ce transport est optimisé pour les communications entre WCF et WCF.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>   
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>   
 <xref:System.ServiceModel.Channels.TransportBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Transports](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [Choix d'un transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)