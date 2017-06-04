---
title: "&lt;clear&gt;, &#233;l&#233;ment de &lt;claimTypeRequirements&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;clear&gt;, &#233;l&#233;ment de &lt;claimTypeRequirements&gt;
Indique que tous les types de revendications doivent être supprimés dans les informations d'identification fédérées.  Cela garantit que la collection est vide au démarrage.  
  
## Syntaxe  
  
```  
  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
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
|[\<claimTypeRequirements\>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|Spécifie une collection de types de revendications requis.  Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.  Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.  Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.|  
  
## Voir aussi  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>   
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>   
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>   
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>   
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>