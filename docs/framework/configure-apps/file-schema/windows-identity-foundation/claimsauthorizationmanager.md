---
title: "&lt;claimsAuthorizationManager&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;claimsAuthorizationManager&gt;
Inscrit un gestionnaire d'autorisations de sinistres pour les demandes entrantes.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Un type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe.  Pour plus d'informations sur la façon de spécifier la `type` d'attribut, consultez [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences).|  
  
### Éléments enfants  
 S'il y a aucun `type` attribut, ou si la `type` références d'attribut du <xref:System.Security.Claims.ClaimsAuthenticationManager> \(classe\), le `<claimsAuthorizationManager>` élément ne prend pas d'éléments enfants ; Toutefois, les classes dérivées de <xref:System.Security.Claims.ClaimsAuthorizationManager> pouvez définir des éléments de configuration enfants.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Spécifie les paramètres d'identité au niveau de service.|  
  
## Notes  
 Le comportement par défaut fourni par le biais de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe autorise toujours les revendications entrantes.  Si aucun `type` attribut est spécifié ou si la `type` attribut spécifie le <xref:System.Security.Claims.ClaimsAuthorizationManager> \(classe\), le `<claimsAuthorizationManager>` élément ne prend pas d'éléments enfants.  Vous pouvez spécifier la `type` attribut pour enregistrer un type dérivé de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe pour implémenter un comportement personnalisé.  Les classes dérivées peuvent prendre en charge de configuration via les éléments enfants de le `<claimsAuthorizationManager>` élément en substituant la <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> méthode pour traiter ces éléments.  Le schéma défini pour les éléments enfants est le Concepteur de la classe.  
  
> [!IMPORTANT]
>  Lorsque vous utilisez le <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou le <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe pour fournir un contrôle d'accès basé sur les revendications dans votre code, la configuration de l'identité qui est référencée par le `<federationConfiguration>` élément configure le Gestionnaire de demandes d'autorisations et la stratégie qui est utilisé pour prendre des décisions d'autorisation.  Ceci est vrai même dans les scénarios qui ne sont pas les scénarios Web passifs, par exemple les applications Windows Communication Foundation \(WCF\) ou une application qui n'est pas basé sur le Web.  Si l'application n'est pas une application Web passive, la `<claimsAuthorizationManager>` élément \(et ses éléments de stratégie enfant, le cas échéant\) de la configuration de l'identité référencées sont les seuls paramètres appliqués.  Tous les autres paramètres sont ignorés.  Pour plus d'informations, consultez l'élément [\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md).  
  
 Cet élément définit le <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=fullName> propriété.  
  
## Exemple  
 Le code XML suivant montre la configuration d'une autorisation de revendications manager qui implémente la stratégie composé de paires de ressource\-action, dont chacun spécifie des combinaisons booléennes des revendications qu'un demandeur doit posséder pour exécuter l'action sur la ressource.  Le code qui implémente le Gestionnaire d'autorisations revendications capable d'utiliser cette stratégie peut être trouvé dans le `ClaimsBasedAuthorization` exemple.  
  
```  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```