---
title: "&lt;announcementEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;announcementEndpoint&gt;
Cet élément de configuration définit un point de terminaison standard avec un contrat d'annonce fixe.  Un service peut éventuellement annoncer sa disponibilité en envoyant un message d'annonce en ligne ou hors connexion selon qu'il est respectivement ouvert ou fermé.  Un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] spécifie les points de terminaison d'annonce dans l'élément [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) et utilise AnnouncementClient pour effectuer les annonces.  Un client qui souhaite écouter l'annonce provenant d'un autre service joue en fait le rôle de service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ; vous devez donc configurer les points de terminaison d'annonce pour ce client dans la section [\<services\>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md).  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <announcementEndpoint>   
          <standardEndpoint  
                  discoveryVersion=”WSDiscovery11/WSDiscoveryApril2005”  
                  maxAnnouncementDelay=”Timespan”   
                  name="String" />   
       </announcementEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|discoveryVersion|Chaîne qui spécifie l'une des deux versions du protocole WS\-Discovery.  Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.  Cette valeur est de type <xref:System.ServiceModel.Discovery.Configuration.DiscoveryVersion>.|  
|maxAnnouncementDelay|Valeur Timespan qui spécifie le délai d'attente maximal du protocole de découverte avant l'envoi d'un message de type Hello.  Les messages attendent pendant un délai aléatoire compris entre 0 et la valeur de cet attribut avant d'être envoyés.  Cet attribut permet de définir un délai court et aléatoire pour empêcher toute tempête de réseau lorsqu'un réseau est en panne et que tous les services reviennent en ligne en même temps.|  
|name|Chaîne qui spécifie le nom de la configuration du point de terminaison standard.  Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés \(adresse, liaison, contrat\) sont fixes.|  
  
## Exemple  
 L'exemple suivant montre un client qui écoute des messages d'annonce sur HTTP et Peernet.  
  
```  
  
<services>  
  <service name="ServiceAnnouncementListener">  
              <endpoint name="httpAnnouncementEndpoint"  
                        kind="announcementEndpoint"  
                        binding="basicHttpBinding"  
                        address="announcements" />  
              <endpoint name="peerNetAnnouncementEndpoint"  
                        kind="announcementEndpoint"  
                        binding="peerTcpBinding"  
                        address="net.p2p://discoveryMesh/multicast"  
                        bindingConfiguration="discoveryPeerTcpBindingConfig" />  
  ...  
  </service>  
</services>  
  
<standardEndpoints>  
  <announcementEndpoint>  
     <standardEndpoint name="httpAnnouncementEndpoint"                         
                       version="WSDiscoveryApril2005" />  
     <standardEndpoint name="peerNetAnnouncementEndpoint"                         
                       version="WSDiscoveryApril2005" />  
   </announcementEndpoint>  
</standardEndpoints>  
  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>