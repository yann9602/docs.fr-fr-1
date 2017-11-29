---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: be98c93452c9c7a37ecad5b03f5160ea08f2c82e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;securityTokenHandlerConfiguration&gt;
Fournit la configuration de la collection de gestionnaires de jetons.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|saveBootstrapContext|Spécifie si les jetons d’amorçage doivent être inclus dans le jeton de session. La valeur peut également être définie sur une collection de gestionnaire de jetons en définissant le `saveBootstrapContext` de l’attribut le [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément. Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.|  
|maximumClockSkew|Un <xref:System.TimeSpan> qui spécifie l’inclinaison d’horloge maximale autorisée. Contrôle l’inclinaison d’horloge maximale autorisée lorsque vous effectuez des opérations sensibles, telles que la validation de l’heure d’expiration d’une session de connexion. La valeur par défaut est 5 minutes, « 00 : 05:00 ». Pour plus d’informations sur la façon de spécifier <xref:System.TimeSpan> valeurs, consultez [valeurs Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). L’inclinaison d’horloge maximale peut également être définie au niveau du service en définissant le `maximumClockSkew` de l’attribut le [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément. Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Spécifie le jeu d’URI qui sont des identificateurs acceptables de cette partie de confiance. Facultatif.|  
|[\<met en cache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Inscrit le met en cache utilisés pour les jetons de session et de la détection de relecture de jetons. Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité. Facultatif.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Contrôle les paramètres qui utilisent des gestionnaires de jetons pour valider les certificats. Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité. Ces paramètres sont remplacés si un gestionnaire spécifique est configuré avec son propre validateur. Facultatif.|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Configure le Registre de nom de l’émetteur qui est utilisé par les gestionnaires de la collection du Gestionnaire de jetons. Facultatif.|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Inscrit le résolveur de jeton de l’émetteur qui est utilisé par les gestionnaires de la collection du Gestionnaire de jetons. Le programme de résolution de jeton de l’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrant. Facultatif.|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Inscrit le résolveur de jeton de service qui est utilisé par les gestionnaires de la collection du Gestionnaire de jetons. Le programme de résolution de jeton de service permet de résoudre le jeton de chiffrement sur les jetons et les messages entrant. Facultatif.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Active la détection de relecture de jetons et spécifie le délai d’expiration pour les jetons. Peut être spécifié au niveau du service ou une collection de gestionnaire de jetons de sécurité. Facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jetons de sécurité qui sont enregistrés avec le point de terminaison.|  
  
## <a name="remarks"></a>Remarques  
 Cette section fournit des valeurs de propriété d’un <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objet. Les paramètres configurés dans cette section remplacent ceux configurés sur le service. Certains de ces paramètres peuvent, à son tour, être remplacée par les paramètres spécifiés quand un gestionnaire est ajouté à la collection de gestionnaire de jetons de sécurité.  
  
## <a name="example"></a>Exemple  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
