---
title: "&lt;namedPipeTransport&gt; | Microsoft Docs"
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
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;namedPipeTransport&gt;
Définit un transport qui entraîne un canal à transférer des messages à l'aide de canaux nommés lorsqu'il est inclus dans une liaison personnalisée.  
  
## Syntaxe  
  
```  
  
<namedPipeTransport>  
      <connectionPoolSettings  
         groupName=”String”  
          idleTimeout"TimeSpan"  
        maxOutboundConnectionsPerEndpopint=”Integer” />  
</namedPipeTransport>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<connectionPoolSettings\> de \<namedPipeTransport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|Spécifie des paramètres de pool de connexions supplémentaires pour une liaison de canal nommé.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Notes  
 Ce transport utilise des URI au format "net.pipe:\/\/nom\_hôte\/chemin".  Les autres composants URI sont facultatifs.  
  
 L'élément `namedPipeTransport` constitue le point de départ pour créer une liaison personnalisée qui implémente le protocole de transport des canaux nommés.  Ce transport est utilisé pour la communication entre WCF \(Windows Communication Foundation\) et WCF sur des ordinateurs.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
 <xref:System.ServiceModel.Channels.TransportBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Transports](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [Choix d'un transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)