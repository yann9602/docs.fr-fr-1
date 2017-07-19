---
title: "&lt;connectionPoolSettings&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;connectionPoolSettings&gt;
Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.  
  
## Syntaxe  
  
```  
  
<connectionPoolSettings  
        groupName=”String”  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint=”Integer” />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`groupName`|Chaîne qui définit le nom du pool de connexions utilisé pour les canaux sortants.  En mode de transmission continu, les connexions ne sont pas partagées, ce qui signifie que la mise en pool des connexions est désactivée.  La valeur par défaut est une chaîne par défaut.  Vous pouvez modifier cette valeur pour isoler les connexions d'un client particulier dans des groupes séparés.|  
|`idleTimeout`|<xref:System.TimeSpan> positif qui spécifie la période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.  La valeur par défaut est 00:02:00.|  
|`maxOutboundConnectionsPerEndpoint`|Entier positif qui spécifie le nombre maximal de connexions à un point de terminaison distant initié par le service.  Toute connexion dépassant cette limite est mise en file d'attente jusqu'à ce qu'une place se libère.  `idleTimeout` limite la durée pendant laquelle les connexions restent dans la file d'attente avant qu'une exception soit levée.  La valeur par défaut est 10.<br /><br /> Cet attribut limite le nombre de connexions actives simultanées entre le client et un point de terminaison de service particulier.  Si cette valeur est dépassée, il est possible que le service ne semble pas répondre au client.  Dans ce cas, cette valeur doit être ajustée de façon à être supérieure au nombre maximal de connexions simultanées prévues à un point de terminaison spécifique.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<namedPipeTransport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>   
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>   
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>   
 <xref:System.ServiceModel.Channels.TransportBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Transports](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [Choix d'un transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)