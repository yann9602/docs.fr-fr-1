---
title: '&lt;identityConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b1cca286fc967631c60aa02a1318fe24120e05b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
Spécifie les paramètres d’identité au niveau du service.  
  
 \<system.identityModel >  
\<identityConfiguration >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Le nom de la section de configuration d’identité. Vous pouvez utiliser ce nom pour faire référence à une section de configuration spécifique. Si aucun `name` attribut est spécifié, la section définit la configuration par défaut. La configuration par défaut est toujours utilisée pour les scénarios de fédération passive. Pour plus d’informations, consultez la [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) élément.|  
|saveBootstrapContext|Spécifie si les jetons d’amorçage doivent être inclus dans le jeton de session. La valeur peut également être définie sur une collection de gestionnaire de jetons en définissant le `saveBootstrapContext` de l’attribut le [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) élément. Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.|  
|maximumClockSkew|Un <xref:System.TimeSpan> qui spécifie l’inclinaison d’horloge maximale autorisée. Contrôle l’inclinaison d’horloge maximale autorisée lorsque vous effectuez des opérations sensibles, telles que la validation de l’heure d’expiration d’une session de connexion. La valeur par défaut est 5 minutes, « 00 : 05:00 ». Pour plus d’informations sur la façon de spécifier <xref:System.TimeSpan> valeurs, consultez [valeurs Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). L’inclinaison d’horloge maximale peut également être définie sur une collection de gestionnaire de jetons en définissant le `maximumClockSkew` de l’attribut le [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) élément. Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<met en cache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Inscrit le met en cache utilisés pour les jetons de session et de la détection de relecture de jetons. Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité. Facultatif.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Contrôle les paramètres qui utilisent des gestionnaires de jetons pour valider les certificats. Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité. Facultatif.|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Inscrit un gestionnaire de l’authentification par revendications pour les revendications entrantes. Facultatif.|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Inscrit un gestionnaire d’autorisation de revendications pour les revendications entrantes. Facultatif.|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Spécifie le jeu de revendications requises pour les jetons de sécurité entrants. Facultatif.|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jetons de sécurité. Zéro ou plusieurs collections de gestionnaires de jetons de sécurité peuvent être spécifiées. Facultatif.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Active la détection de relecture de jetons et spécifie le délai d’expiration pour les jetons. Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité. Facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Fournit la configuration pour activer les options de Windows Identity Foundation (WIF) dans les applications.|  
  
## <a name="remarks"></a>Remarques  
 Identité de plusieurs configurations peuvent être définies, chacun avec un nom unique. Le comportement est comme suit :  
  
1.  Si aucun `<identityConfiguration>` élément est spécifié. Une configuration d’identité par défaut est créée lors de l’exécution et remplie avec les valeurs par défaut.  
  
2.  Si un seul `<identityConfiguration>` élément est spécifié. Il s’agit de la configuration d’identité par défaut. S’il est nommé ou sans nom n’a pas d’importance.  
  
3.  Si plusieurs `<identityConfiguration>` éléments sont spécifiés. L’élément sans nom spécifie la configuration d’identité par défaut. Il est recommandé que lorsque vous spécifiez plusieurs `<identityConfiguration>` des éléments, un d’eux doit être sans nom.  
  
> [!WARNING]
>  Si vous spécifiez plusieurs `<identityConfiguration>` des éléments, un d’eux doit être sans nom. L’élément sans nom sera la configuration d’identité par défaut.  
  
 Certains des paramètres spécifiés dans le `<identityConfiguration>` élément peut être remplacé par les paramètres sur une collection de gestionnaire de jetons de sécurité ou par les paramètres sur les gestionnaires de jetons de sécurité individuels.  
  
> [!IMPORTANT]
>  Lorsque vous utilisez la <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou le <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe pour fournir un contrôle d’accès basé sur les revendications dans votre code, la configuration d’identité qui est référencée par le `<federationConfiguration>` élément configure le Gestionnaire d’autorisations de revendications et une stratégie qui est utilisé pour effectuer décisions d’autorisation. Cela est vrai, même dans les scénarios qui ne sont pas des scénarios de Web passifs, par exemple les applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web. Si l’application n’est pas une application Web passive, le [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) élément (et ses éléments de stratégie enfants, le cas échéant) de la configuration de l’identité référencée sont les seuls paramètres appliqués. Tous les autres paramètres sont ignorés. Pour plus d’informations, consultez la [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) élément.  
  
 Le `<identityConfiguration>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> classe. Une section de configuration d’identité est représentée par la <xref:System.IdentityModel.Configuration.IdentityConfiguration> classe.  
  
> [!IMPORTANT]
>  En spécifiant les éléments suivants en tant qu’éléments enfants de le `<identityConfiguration>` élément a été déconseillé, même si le comportement est toujours prise en charge pour la compatibilité descendante. Ces éléments doivent, au lieu de cela, être spécifiés sous la [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) élément.  
>   
>  -   [\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une configuration d’identité nommée « alternateConfiguration ». La configuration d’identité spécifie les paramètres par défaut.  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
