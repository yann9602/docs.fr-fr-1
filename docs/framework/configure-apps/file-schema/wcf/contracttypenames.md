---
title: "&lt;contractTypeNames&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;contractTypeNames&gt;
Section de configuration qui spécifie une liste de noms de type de contrat, qui sont les noms de contrat des services recherchés, et les critères généralement utilisés lors de la recherche d'un service.  Si plusieurs noms de contrat sont spécifiés, seuls les points de terminaison de service correspondant à TOUS les contrats répondent.  Notez que dans [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], un point de terminaison ne peut prendre en charge qu'un seul contrat.  
  
## Syntaxe  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <dynamicEndpoint>   
          <standardEndpoint>  
             <discoveryClientSettings discoveryEndpoint=”String” >  
               <findCriteria duration=”TimeSpan”  
                  maxResults=”Integer”   
                  scopeMatchBy=”Uri” >  
                  <contractTypeNames>  
                     <add name="String" namespace="String" />  
                  <contractTypeNames>  
                  <extensions />  
                  <scopes>  
                    <add scope="URI"/>  
                  </scopes>  
               </findCriteria>  
             </discoveryClientSettings>  
          <standardEndpoint>  
       </dynamicEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Un nom de type de contrat est une propriété qui fait référence au jeu de critères utilisé en général au cours de la recherche d'un service.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<findCriteria\>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.  Les critères peuvent être regroupés en critères de recherche \(spécifiant les services recherchés\) et critères d'arrêt de la recherche \(durée de la recherche\).|  
  
## Voir aussi  
 <xref:System.ServiceModel.Discovery.FindCriteria>   
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>   
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>