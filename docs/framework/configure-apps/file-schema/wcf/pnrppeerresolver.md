---
title: "&lt;pnrpPeerResolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;pnrpPeerResolver&gt;
Spécifie que le programme de résolution PNRP \(Peer Name Resolution Protocol\) doit être utilisé comme un programme de résolution.  Cet élément est facultatif parce que PNRP est le programme de résolution par défaut.  
  
## Syntaxe  
  
```  
  
<pnrpResolver resolverType="String" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|resolverType|Chaîne qui spécifie le programme de résolution à utiliser.  Cet attribut est facultatif.  S'il n'est pas défini ou s'il a pour valeur une chaîne vide, PNRP est utilisé.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Exemple  
  
```  
<pnrpResolver resolverType="" />  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>   
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [Programmes de résolution d'homologue](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)