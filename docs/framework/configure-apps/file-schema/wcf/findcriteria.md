---
title: "&lt;findCriteria&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;findCriteria&gt;
Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.  Les critères peuvent être regroupés en critères de recherche \(spécifiant les services recherchés\) et critères d'arrêt de la recherche \(durée de la recherche\).  
  
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
  
|Attribut|Description|  
|--------------|-----------------|  
|duration|Valeur Timespan qui spécifie le temps d'attente maximal des réponses envoyées par les services sur le réseau.  La durée par défaut est de 20 secondes.|  
|maxResults|Entier qui spécifie le nombre maximal de réponses à attendre en provenance des services sur un réseau ou sur Internet.  Si le nombre maximal de réponses est reçu avant l'écoulement du délai d'attente spécifié dans l'attribut `duration`, l'opération de recherche prend fin.|  
|scopeMatchBy|URI qui spécifie l'algorithme de correspondance à utiliser, lors de la comparaison des portées dans le message Probe avec celles du point de terminaison.<br /><br /> Il existe cinq règles de correspondance de portée prises en charge.  Si vous ne spécifiez pas de règle de correspondance de portée, `ScopeMatchByPrefix` est utilisé.  Pour plus d'informations, consultez <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<contractTypeNames\>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Collection d'éléments de configuration qui contiennent les noms des types de contrat de service de flux de travail.|  
|\<extensions\> de \<findCriteria\>|Collection d'objets d'élément XML qui fournissent des extensions.|  
|[\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Collection d'objets qui contiennent des URI absolus utilisés pendant une opération de recherche afin de localiser des services ou un service particulier.<br /><br /> Si le service particulier est trouvé, une correspondance réussie est établie entre l'URI de service et l'URI de portée, parfois à l'aide de règles de portée qui gèrent les problèmes de correspondance.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Discovery.FindCriteria>   
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>