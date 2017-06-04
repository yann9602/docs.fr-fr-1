---
title: "&lt;authorizationPolicies&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;authorizationPolicies&gt;
Cette section de configuration contient une collection des types de stratégie d'autorisation, qui peuvent être ajoutés à l'aide du mot clé `add`.  Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.  L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.  Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.  Pour plus d'informations sur le fonctionnement d'une stratégie d'autorisation, consultez <xref:System.IdentityModel.Policy.IAuthorizationPolicy> et [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
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
 [\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)   
 [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md)