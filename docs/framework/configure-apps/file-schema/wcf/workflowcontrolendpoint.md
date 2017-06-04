---
title: "&lt;workflowControlEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;workflowControlEndpoint&gt;
Cet élément de configuration définit un point de terminaison standard permettant de contrôler l'exécution d'instances de flux de travail \(créer, exécuter, interrompre, arrêter, etc.\).  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <workflowControlEndpoint>   
          <standardEndpoint  
                  name="String" />   
       </workflowControlEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Chaîne qui spécifie le nom de la configuration du point de terminaison standard.  Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés \(adresse, liaison, contrat\) sont fixes.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Activites.WorkflowControlEndpoint>