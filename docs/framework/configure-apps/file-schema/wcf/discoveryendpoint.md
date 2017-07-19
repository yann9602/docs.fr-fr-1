---
title: "&lt;discoveryEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;discoveryEndpoint&gt;
Cet élément de configuration définit un point de terminaison standard avec un contrat de découverte fixe.  Lorsqu'il est ajouté à la configuration du service, il spécifie où écouter les messages de découverte.  Lorsqu'il est ajouté à la configuration client, il spécifie où envoyer les requêtes de découverte.  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <discoveryEndpoint>   
          <standardEndpoint  
                  discoveryMode=”Adhoc/Managed”  
                  discoveryVersion=”WSDiscovery11/WSDiscoveryApril2005”  
                  maxResponseDelay=”Timespan”   
                  name="String" />  
       </discoveryEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|discoveryMode|Chaîne qui spécifie le mode de protocole de découverte.  Les valeurs valides sont « Ad hoc » et « Managé ».  En mode managé, le protocole repose sur un proxy de découverte, qui fait office de référentiel des services détectables.  Le mode ad hoc nécessite que le protocole utilise le mécanisme de multidiffusion UDP pour rechercher les services disponibles.  Cette valeur est de type <xref:System.Servicemodel.Discovery.DiscoveryMode>.|  
|discoveryVersion|Chaîne qui spécifie l'une des deux versions du protocole WS\-Discovery.  Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005.  Cette valeur est de type <xref:System.Servicemodel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Valeur Timespan qui indique la valeur maximale du délai d'attente du protocole de découverte avant l'envoi de certains messages, tels que ceux de type Probe Match ou Resolve Match.<br /><br /> Si tous les messages ProbeMatches sont envoyés en même temps, une tempête de réseau peut en résulter.  Pour empêcher cet effet, les messages ProbeMatches sont envoyés avec un délai aléatoire entre chaque message ProbeMatch.  Le délai aléatoire est compris entre 0 et la valeur définie par cet attribut.  Si l'attribut a la valeur 0, les messages ProbeMatches sont envoyés dans une boucle serrée sans délai.  Sinon, les messages ProbeMatches sont envoyés avec un délai aléatoire de sorte que la durée totale nécessaire à l'envoi de tous les messages ProbeMatches ne dépasse pas le maxResponseDelay.  Cette valeur est uniquement pertinente pour les services, elle n'est pas utilisée par les clients.|  
|`name`|Chaîne qui spécifie le nom de la configuration du point de terminaison standard.  Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés \(adresse, liaison, contrat\) sont fixes.|  
  
## Exemple  
 L'exemple suivant montre un service qui écoute des messages de découverte sur un transport de multidiffusion Peernet.  L'exemple spécifie de manière explicite la version WS\-Discovery Avril 2005.  
  
 La configuration du point de terminaison standard est définie par service et ne peut pas être partagée entre les services.  Si un autre service souhaite avoir le même point de terminaison de découverte, la même configuration doit être ajoutée à la section de ce service.  
  
```  
  
<services>  
    <service name="CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
             <endpoint binding="basicHttpBinding"   
                address="calculator" contract="ICalculatorService" />  
             <endpoint name="peerNetDiscovery"  
                binding="peerTcpBinding"  
                address="net.p2p://discoveryMesh/multicast"  
                kind="discoveryEndpoint"  
                endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"  
                bindingConfiguration="discoveryPeerTcpBindingConfig" />      
   </service>  
</services>  
<standardEndpoints>  
  <discoveryEndpoint>  
     <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration "                         
                       version="WSDiscoveryApril2005" />  
   </discoveryEndpoint>  
</standardEndpoints>  
  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>