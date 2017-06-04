---
title: "&lt;services&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;services&gt;
Les services sont définis dans la section `services` du fichier de configuration.  Chacun dispose de sa propre section de configuration de `service`.  
  
 \<system.ServiceModel\>  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 None  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<service\>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Définissez le contrat de service, le comportement et les points de terminaison du service particulier.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Élément racine de tous les éléments de configuration Windows Communication Foundation \(WCF\).|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ServicesSection>