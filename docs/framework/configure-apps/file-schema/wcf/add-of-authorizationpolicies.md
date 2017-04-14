---
title: "&lt;add&gt; de &lt;authorizationPolicies&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &lt;add&gt; de &lt;authorizationPolicies&gt;
Spécifie une stratégie d'autorisation pour la transformation de revendications.  
  
## Syntaxe  
  
```  
  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## Type  
 `Type`  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`policyType`|Attribut String requis.<br /><br /> Le modèle de contrôle d'accès de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] prend en charge la configuration d'un ensemble de stratégies d'autorisation en tant que types.  Cet attribut spécifie une stratégie d'autorisation qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.  Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<authorizationPolicies\>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|Indique une collection de types de stratégie d'autorisation.|  
  
## Notes  
 Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.  L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.  Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.  Pour plus d'informations sur le fonctionnement d'une stratégie d'autorisation, consultez <xref:System.IdentityModel.Policy.IAuthorizationPolicy> et [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>   
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>   
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>   
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>   
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>   
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>   
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>   
 [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)   
 [Comment : créer un gestionnaire d'autorisations personnalisé pour un service](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)   
 [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md)