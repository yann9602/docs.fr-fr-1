---
title: '&lt;claimsAuthorizationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: eb0475796a488489f4a32c820d1a92994237d7fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimsauthorizationmanagergt"></a>&lt;claimsAuthorizationManager&gt;
Inscrit un gestionnaire d’autorisation de revendications pour les revendications entrantes.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<claimsAuthorizationManager >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Un type personnalisé qui dérive de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe. Pour plus d’informations sur la façon de spécifier le `type` d’attribut, consultez [références de Type personnalisé](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 S’il existe aucune `type` attribut, ou si le `type` les références d’attribut le <xref:System.Security.Claims.ClaimsAuthenticationManager> (classe), le `<claimsAuthorizationManager>` élément ne prend pas d’éléments enfants ; Toutefois, les classes dérivées de <xref:System.Security.Claims.ClaimsAuthorizationManager> peut définir des éléments de configuration enfants.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
  
## <a name="remarks"></a>Notes  
 Le comportement par défaut fourni par le biais du <xref:System.Security.Claims.ClaimsAuthorizationManager> classe autorise toujours les revendications entrantes. Si aucun `type` attribut est spécifié ou si le `type` attribut spécifie la <xref:System.Security.Claims.ClaimsAuthorizationManager> (classe), le `<claimsAuthorizationManager>` élément ne prend pas d’éléments enfants. Vous pouvez spécifier le `type` attribut pour enregistrer un type dérivé de la <xref:System.Security.Claims.ClaimsAuthorizationManager> classe pour implémenter un comportement personnalisé. Les classes dérivées peuvent prendre en charge la configuration par le biais des éléments enfants de la `<claimsAuthorizationManager>` élément en remplaçant le <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> méthode pour gérer ces éléments. Le schéma défini pour les éléments enfants est sur le Concepteur de la classe.  
  
> [!IMPORTANT]
>  Lorsque vous utilisez la <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou le <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe pour fournir un contrôle d’accès basé sur les revendications dans votre code, la configuration d’identité qui est référencée par le `<federationConfiguration>` élément configure le Gestionnaire d’autorisations de revendications et une stratégie qui est utilisé pour effectuer décisions d’autorisation. Cela est vrai, même dans les scénarios qui ne sont pas des scénarios de Web passifs, par exemple les applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web. Si l’application n’est pas une application Web passive, le `<claimsAuthorizationManager>` élément (et ses éléments de stratégie enfants, le cas échéant) de la configuration de l’identité référencée sont les seuls paramètres appliqués. Tous les autres paramètres sont ignorés. Pour plus d’informations, consultez la [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) élément.  
  
 Cet élément définit les <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriété.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre la configuration d’une autorisation de revendications gestionnaire qui implémente la stratégie composé de paires d’action de ressource qui spécifient chacune des combinaisons booléennes des revendications comportant un demandeur doit effectuer l’action sur la ressource. Le code qui implémente le Gestionnaire d’autorisations revendications capable d’utiliser cette stratégie peut être trouvé dans le `ClaimsBasedAuthorization` exemple.  
  
```xml  
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
