---
title: "&lt;webScriptEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;webScriptEndpoint&gt;
Cet élément de configuration définit un point de terminaison standard avec une liaison [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) fixe qui ajoute automatiquement le comportement [\<enableWebScript\>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md).  Utilisez ce point de terminaison lorsque vous écrivez un service appelé à partir d'une application ASP.NET AJAX.  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <webScriptEndpoint>   
          <standardEndpoint  
             webEndpointType=”String”/>        
       </webScriptEndpoint>   
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|webEndpointType|Chaîne qui spécifie le type du point de terminaison.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés \(adresse, liaison, contrat\) sont fixes.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>   
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>