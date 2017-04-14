---
title: "&lt;claimsAuthenticationManager&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;claimsAuthenticationManager&gt;
Enregistre un gestionnaire d'authentification des revendications pour les revendications entrantes.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|type|Spécifie un type personnalisé qui dérive de la classe d' <xref:System.Security.Claims.ClaimsAuthenticationManager> .  Pour plus d'informations sur la spécification de l'attribut d' `type` , consultez [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferencess).|  
  
### Éléments enfants  
 S'il n'y a aucun attribut d' `type` , ou si l'attribut référence d' `type` la classe d' <xref:System.Security.Claims.ClaimsAuthenticationManager> , l'élément d' `<claimsAuthenticationManager>` ne prend pas d'éléments enfants ; toutefois, les classes dérivées d' <xref:System.Security.Claims.ClaimsAuthenticationManager> peuvent définir des éléments de configuration enfants.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Spécifie des paramètres d'identité au niveau de le service.|  
  
## Notes  
 Le comportement par défaut fournie par la classe d' <xref:System.Security.Claims.ClaimsAuthenticationManager> répercute les revendications entrantes.  Si aucun attribut d' `type` n'est spécifié ou si l'attribut d' `type` spécifie la classe d' <xref:System.Security.Claims.ClaimsAuthenticationManager> , l'élément d' `<claimsAuthenticationManager>` ne prend pas d'éléments enfants.  Vous pouvez spécifier l'attribut pour `type` pour stocker un type dérivé de la classe d' <xref:System.Security.Claims.ClaimsAuthenticationManager> pour implémenter un comportement personnalisé.  Les classes dérivées peuvent prendre en charge la configuration à l'aide de éléments enfants de l'élément d' `<claimsAuthenticationManager>` en substituant la méthode d' <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> pour gérer ces éléments.  Le schéma défini pour les éléments enfants est au concepteur de la classe.  
  
 L'élément définit d' `<claimsAuthenticationManager>` la propriété d' <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=fullName> .  
  
## Exemple  
  
```  
<system.identityModel>  
    <identityConfiguration name=”MyIdentity”>  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```