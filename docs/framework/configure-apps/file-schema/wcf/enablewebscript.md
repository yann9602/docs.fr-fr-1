---
title: "&lt;enableWebScript&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;enableWebScript&gt;
Cet élément active le comportement de point de terminaison qui permet de consommer le service à partir de pages Web ASP.NET AJAX.  
  
## Syntaxe  
  
```  
  
<enableWebScript />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie le jeu de comportements du point de terminaison.|  
  
## Notes  
 Ce comportement doit être utilisé uniquement avec la liaison standard [\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) ou avec l'élément de liaison [\<webMessageEncoding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md).  Pour plus d'informations sur ce comportement, consultez <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>   
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>   
 [Intégration d'AJAX et prise en charge de JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)   
 [\<webHttp\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)