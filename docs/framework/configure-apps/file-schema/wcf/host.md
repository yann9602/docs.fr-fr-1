---
title: "&lt;h&#244;te&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;h&#244;te&gt;
Spécifie les paramètres d'un hôte de service.  
  
## Syntaxe  
  
```  
  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## Type  
 `Type`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<baseAddresses\>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Collection d'éléments `baseAddress` qui spécifie les adresses de base utilisées par l'hôte de service.|  
|[\<timeOuts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|Élément de configuration qui spécifie la durée d'ouverture ou de fermeture autorisée de l'hôte de service.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<service\>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Spécifie les paramètres d'un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.HostElement>   
 <xref:System.ServiceModel.ServiceHost>   
 [Hébergement](../../../../../docs/framework/wcf/feature-details/hosting.md)