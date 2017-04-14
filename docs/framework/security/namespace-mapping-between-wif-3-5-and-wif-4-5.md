---
title: "Mappage des espaces de noms entre WIF&#160;3.5 et WIF&#160;4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# Mappage des espaces de noms entre WIF&#160;3.5 et WIF&#160;4.5
Depuis le.NET 4,5, IDENTITY Windows Foundation \(WIF\) a été entièrement intégré dans le .NET Framework.  Les modifications de nom engendrés par cette intégration et de la fusion des espaces de noms WIF et la surface l'API.  Cette rubrique fournit de l'aide et un mappage général entre les espaces de noms WIF 3,5 et les espaces de noms WIF 4,5.  Il n'est pas destiné à être approfondi, mais plutôt fournit des informations générales concernant l'emplacement où rechercher les classes familières de WIF 3,5 dans WIF 4,5.  Pour plus d'informations sur les différences entre les WIF 3,5 et WIF 4,5, consultez [Nouveautés de Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md).  Pour obtenir de l'aide sur la migration des applications créées à l'aide de WIF WIF 3,5 à 4,5, consultez [Recommandations sur la migration d’une application générée à l’aide de WIF 3.5 à WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
## Mappage d'espace de noms WIF 3,5 à 4,5 WIF  
 Les classes de WIF, collectées dans les espaces de noms d' `Microsoft.IdentityModel` dans WIF 3,5, sont désormais distribuées entre les espaces de noms suivants : `System.Security.Claims`, `System.ServiceModel.Security`, les espaces de noms d' `System.IdentityModel` dans WIF 4,5.  En outre les espaces de noms d'un certain WIF 3,5 ont été consolidés ou complètement supprimés dans WIF 4,5.  
  
> [!IMPORTANT]
>  Les espaces de noms suivants d' `System.IdentityModel` contiennent des classes qui implémentent le modèle d'identité basé sur revendications WCF : <xref:System.IdentityModel.Claims?displayProperty=fullName>, <xref:System.IdentityModel.Policy?displayProperty=fullName>, et <xref:System.IdentityModel.Selectors?displayProperty=fullName>.  Le modèle d'identité basé sur revendications WCF est remplacé par WIF.  Vous ne devez pas utiliser les classes dans ces trois espaces de noms en générant des solutions sur WIF.  
  
 Le tableau suivant fournit des informations concernant l'emplacement où les classes de WIF 3,5 se trouvent dans WIF 4,5.  
  
||||  
|-|-|-|  
|**L'espace de noms WIF 3,5**|**L'espace de noms WIF 4,5**|**Commentaires**|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=fullName>|-   La plupart des classes qui représentent les constantes ne sont pas implémentées.<br />-   Les classes utilisées pour générer des services d'émission de jeton de sécurité ont été déplacées d' `Microsoft.IdentityModel.SecurityTokenService` à <xref:System.IdentityModel?displayProperty=fullName>.<br />-   Les classes de `Microsoft.IdentityModel.Threading` ont été déplacées vers <xref:System.IdentityModel?displayProperty=fullName>.<br />-   Les classes d' `ExceptionMapper` et d' `MruSecurityTokenCache` ne sont pas implémentées.|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=fullName>|-   Les interfaces d' `IClaimsPrincipal` et d' `IClaimsIdentity` ne sont pas implémentées dans WIF 4,5.  À la place <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> et <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> sont maintenant les classes de base dont la plupart des classes d'entité et d'identité .NET dérivent.  Cela signifie qu'il n'est pas nécessaire de revendications spécialisées entité et de classes d'identité comme `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` et `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` dans WIF 4,5, utilisez <xref:System.Security.Principal.WindowsPrincipal?displayProperty=fullName> et <xref:System.Security.Principal.WindowsIdentity?displayProperty=fullName> à la place.  Il en va de même pour autre pour les autres revendications spécialisées entité et les classes d'identité qui existaient dans WIF 3,5.<br />-   La classe d' `Microsoft.IdentityModel.Claims.ClaimsCollection` n'est pas implémentée dans WIF 4,5.  À la place, les perceptions de revendications sont exposées en tant que collections énumérables de type <xref:System.Security.Claims.Claim?displayProperty=fullName>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> et <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> fournissent des méthodes qui prennent désormais totalement LINQ.|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=fullName>|Certains éléments et classes ont subi des modifications de noms et certains ont été supprimés dans WIF 4,5 ; par exemple `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` est maintenant <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=fullName>.|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Non implémenté dans WIF 4,5|Dans WIF 3,5 contient des classes pour prendre en charge CardSpace, non implémenté dans WIF 4,5.|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|Fractionnement entre <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> et les espaces de noms d' <xref:System.ServiceModel.Security?displayProperty=fullName> .|Les classes qui représente des artefacts de WS\-Trust dans l'espace de noms d' <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> ; par exemple, la classe d' <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> .  Les classes qui représentent des contrats de service WCF, entretiennent des hôtes, et les canaux qui permettent à un service WCF pour communiquer à l'aide de le protocole de WS\-Trust dans l'espace de noms d' <xref:System.ServiceModel.Security?displayProperty=fullName> ; par exemple, la classe d' <xref:System.ServiceModel.Security.WSTrustServiceHost> .|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Non implémenté dans WIF 4,5|\-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Non implémenté dans WIF 4,5|Classes contenues qui représentent des constantes de chiffrement XML dans WIF 3,5.  Ces constantes ne sont pas implémentées dans WIF 4,5.|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=fullName>|La classe et les classes d' `EnvelopingSignature` qui représentent les constantes ne sont pas implémentées.|  
|`Microsoft.IdentityModel.SecurityTokenService`|Fractionner entre <xref:System.IdentityModel?displayProperty=fullName>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>, les espaces de noms d' <xref:System.IdentityModel.Tokens?displayProperty=fullName> .|\-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>|Les classes qui fournissent la configuration pour les scénarios passifs \(WS\-Federation\) ont été principalement déplacées vers <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>; toutefois, certaines de ces classes sont dans <xref:System.IdentityModel.Services?displayProperty=fullName>.|  
|`Microsoft.IdentityModel.Web.Controls`|Non implémenté dans WIF 4,5|Les classes de `Microsoft.IdentityModel.Web.Controls` a implémenté le contrôle de connexion passive fédérée, qui n'existe pas dans WIF 4,5.|  
|`Microsoft.IdentityModel.WindowsTokenService`|Non implémenté dans WIF 4,5|\-|  
  
## Voir aussi  
 [Nouveautés de Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)   
 [Recommandations sur la migration d’une application générée à l’aide de WIF 3.5 à WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)