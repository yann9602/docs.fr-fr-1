---
title: "&lt;endpointExtensions&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;endpointExtensions&gt;
Cette section inscrit un nouveau point de terminaison standard dans la section des extensions du fichier de configuration machine ou d'application.  Vous pouvez ajouter un point de terminaison standard à cette collection à l'aide du mot clé `add` et affecter à l'attribut `type` de l'élément le type du point de terminaison et à l'attribut `name` le nom du point de terminaison standard.  
  
 L'exemple suivant utilise l'élément `add`, ainsi que l'attribut `name`, pour ajouter un point de terminaison standard à la section `<endpointExtensions>` du fichier de configuration.  
  
```  
<system.serviceModel>  
    <extensions>  
        <endpointExtensions>  
           <add name="udpDiscoveryEndpoint"  
                type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
        </endpointExtensions>   
    </extensions>  
</system.serviceModel>  
```  
  
 Après avoir inscrit le point de terminaison standard, vous pouvez l'utiliser comme indiqué dans l'exemple suivant.  Dans l'élément [\<Point de terminaison \(endpoint\)\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md), l'attribut `kind` spécifie le type de point de terminaison standard inscrit dans la section `<endpointExtensions>`.  L'attribut `endpointConfiguration` est identique à l'attribut `name` de l'élément de configuration du point de terminaison standard dans la section `<standardEndpoints>`.  
  
```  
  
<system.serviceModel>  
    <services>  
      <service name="Service1">  
        <endpoint kind="udpDiscoveryEndpoint"  
                  endpointConfiguration="udpConfig" />  
      </service>  
    </services>  
    <standardEndpoints>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
                  name="udpConfig"  
                  multicastAddress="soap.udp://239.255.255.250:3703"  
                  ... />  
      </udpDiscoveryEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
  
```