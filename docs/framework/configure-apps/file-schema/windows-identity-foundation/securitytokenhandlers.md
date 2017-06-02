---
title: "&lt;securityTokenHandlers&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;securityTokenHandlers&gt;
Spécifie une collection de gestionnaires de jeton de sécurité qui sont enregistrés avec le point de terminaison.  
  
## Syntaxe  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Spécifie le nom d'une collection de gestionnaires de jeton.  Les seules valeurs reconnues par l'infrastructure sont « ActAs » et « OnBehalfOf ».  Si les collections de Gestionnaire de jetons sont spécifiées avec un de ces noms, la collection sera utilisée lorsque le traitement ActAs ou OnBehalfOf respectivement les jetons.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Ajoute un gestionnaire de jetons de sécurité à la collection de gestionnaires de jeton.|  
|[\<vide\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Efface tous les gestionnaires de jeton de sécurité à partir de la collection de gestionnaires de jeton.|  
|[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Supprime un gestionnaire de jetons de sécurité de la collection de gestionnaires de jeton.|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Fournit la configuration de la collection de gestionnaires de jetons.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Spécifie les paramètres d'identité au niveau de service.|  
  
## Notes  
 Vous pouvez spécifier une ou plusieurs collections nommées de gestionnaires de jeton de sécurité dans une configuration de service.  Vous pouvez spécifier un nom pour une collection en utilisant la `name` attribut.  Les seuls noms qui gère l'infrastructure sont « ActAs » et « OnBehalfOf ».  Si les gestionnaires d'existent dans ces collections, ils sont utilisés par un service de jeton de sécurité \(STS\) plutôt que des gestionnaires par défaut lors du traitement `ActAs` et `OnBehalfOf` jetons.  
  
 Par défaut, la collection est remplie avec les types de gestionnaires suivants : <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, et <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.  Vous pouvez modifier la collection à l'aide de la `<add>`, `<remove>`, et `<clear>` éléments.  Vous devez vous assurer que seulement un seul gestionnaire d'un type particulier existe dans la collection.  Par exemple, si vous dérivez un gestionnaire à partir de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> de classe, soit votre gestionnaire ou le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> peut être configuré dans une collection unique, mais pas les deux.  
  
 Utilisation du `<securityTokenHandlerConfiguration>` élément pour spécifier les paramètres de configuration pour les gestionnaires dans la collection.  Paramètres spécifiés par l'intermédiaire de cet élément ont priorité sur ceux spécifiés sur le service par le biais de la [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) élément.  Certains gestionnaires \(y compris parmi les types de gestionnaire intégré\) peuvent prendre en charge une configuration supplémentaire via un élément enfant de le `<add>` élément.  Paramètres spécifiés dans un gestionnaire remplacent les paramètres équivalents spécifiés dans la collection ou le service.