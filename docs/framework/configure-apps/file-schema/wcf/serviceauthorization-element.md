---
title: "&lt;serviceAuthorization&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# &lt;serviceAuthorization&gt;, &#233;l&#233;ment
Spécifie les paramètres qui autorisent l'accès pour l'entretien des opérations  
  
## Syntaxe  
  
```  
  
<serviceAuthorization  
     impersonateCallerForAllOperations="Boolean"  
      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"  
      roleProviderName="String"  
      serviceAuthorizationManagerType="String" />  
      <authorizationPolicies>  
         <add policyType="String" />  
      </authorizationPolicies>  
</serviceAuthorization>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|impersonateCallerForAllOperations|Valeur booléenne qui spécifie si toutes les opérations du service personnifient l'appelant.  La valeur par défaut est `false`.<br /><br /> Lorsqu'une opération de service spécifique personnifie l'appelant, le contexte du thread est basculé sur le contexte de l'appelant avant d'exécuter le service spécifié.|  
|principalPermissionMode|Définit la principal de sécurité utilisée pour effectuer les opérations sur le serveur.  Les valeurs sont notamment les suivantes :<br /><br /> -   None<br />-   UseWindowsGroups<br />-   UseAspNetRoles<br />-   Personnalisé<br /><br /> La valeur par défaut est UseWindowsGroups.  La valeur est de type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.  Pour plus d'informations sur l'utilisation de cet attribut, consultez [Comment : restreindre l'accès à l'aide de la classe PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Chaîne qui spécifie le nom du fournisseur de rôles, qui fournit des informations de rôle pour une application de Windows Communication Foundation \(WCF\).  La valeur par défaut est une chaîne vide.|  
|ServiceAuthorizationManagerType|Chaîne qui contient le type du gestionnaire d'autorisations de service.  Pour plus d'informations, consultez <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|authorizationPolicies|Contient une collection des types de la stratégie d'autorisation, qui peuvent être ajoutés à l'aide du mot clé `add`.  Chaque stratégie d'autorisation contient un attribut `policyType` requis unique qui est une chaîne.  L'attribut spécifie une stratégie d'autorisation, qui active la transformation d'un jeu de revendications d'entrée dans un autre jeu de revendications.  Le contrôle d'accès peut être accordé ou refusé en fonction de cette opération.  Pour plus d'informations, consultez <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Contient une collection de paramètres pour le comportement d'un service.|  
  
## Notes  
 Cette section contient des éléments qui affectent l'autorisation, les fournisseurs de rôles personnalisés et l'emprunt d'identité.  
  
 L'attribut `principalPermissionMode` spécifie les groupes d'utilisateurs à utiliser lors de l'autorisation d'utilisation d'une méthode protégée.  La valeur par défaut \(`UseWindowsGroups`\) spécifie qu'une identité essayant d'accéder à une ressource est recherchée dans les groupes Windows, comme Administrateurs ou Utilisateurs.  Vous pouvez également spécifier `UseAspNetRoles` pour utiliser un fournisseur de rôles personnalisé configuré sous l'élément \<system.web\>, tel qu'indiqué dans le code suivant.  
  
```  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 Le code suivant présente le `roleProviderName` utilisé avec l'attribut `principalPermissionMode`.  
  
```  
<behaviors>  
   <behavior name="ServiceBehaviour">  
     <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                           roleProviderName ="SqlProvider" />  
   </behavior>   
<!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
 Pour obtenir un exemple détaillé de l'utilisation de cet élément de configuration, consultez [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) et [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>   
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>   
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)   
 [Comment : créer un gestionnaire d'autorisations personnalisé pour un service](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)   
 [Comment : restreindre l'accès à l'aide de la classe PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)   
 [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md)