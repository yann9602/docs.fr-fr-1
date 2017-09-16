---
title: Mappage des espaces de noms entre WIF 3.5 et WIF 4.5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
caps.latest.revision: 4
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9c3d726ee5b6da733ddaa79ec23943bb6faa43e5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Mappage des espaces de noms entre WIF 3.5 et WIF 4.5
À compter du .NET 4.5, Windows Identity Foundation (WIF) est entièrement intégré au .NET Framework. Cette intégration a entraîné le changement de certains noms, ainsi que la consolidation des espaces de noms WIF et de la surface de l’API. Cette rubrique fournit des instructions et établit une correspondance entre les espaces de noms WIF 3.5 et les espaces de noms WIF 4.5. Il ne s’agit pas d’instructions exhaustives, mais plutôt d’informations générales qui vous permettront de trouver les classes WIF 3.5 avec lesquelles vous êtes familier dans WIF 4.5. Pour plus d’informations sur les différences entre WIF 3.5 et WIF 4.5, consultez [Nouveautés de Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md). Pour obtenir des conseils sur la migration d’une application WIF 3.5 vers WIF 4.5, consultez [Recommandations sur la migration d’une application générée à l’aide de WIF 3.5 à WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
## <a name="wif-35-to-wif-45-namespace-map"></a>Correspondance entre les espaces de noms WIF 3.5 et WIF 4.5  
 Les classes WIF, qui étaient collectées sous les espaces de noms `Microsoft.IdentityModel` dans WIF 3.5, sont désormais distribuées entre les espaces de noms `System.Security.Claims`, `System.ServiceModel.Security` et `System.IdentityModel` dans WIF 4.5. De plus, certains espaces de noms WIF 3.5 ont été regroupés et d’autres supprimés dans WIF 4.5.  
  
> [!IMPORTANT]
>  Les espaces de noms `System.IdentityModel` suivants contiennent des classes qui implémentent le modèle d’identité basé sur des revendications WCF : <xref:System.IdentityModel.Claims?displayProperty=fullName>, <xref:System.IdentityModel.Policy?displayProperty=fullName> et <xref:System.IdentityModel.Selectors?displayProperty=fullName>. Le modèle d'identité basé sur des revendications WCF est remplacé par WIF. Vous ne devez pas utiliser les classes de ces trois espaces de noms quand vous créez des solutions basées sur WIF.  
  
 Le tableau suivant explique où trouver les classes WIF 3.5 dans WIF 4.5.  
  
|**Espace de noms WIF 3.5**|**Espace de noms WIF 4.5**|**Commentaires**|  
|-|-|-|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=fullName>|- La plupart des classes qui représentent des constantes ne sont pas implémentées.<br />- Les classes qui permettent de générer des services d’émission de jeton de sécurité ont été déplacées de `Microsoft.IdentityModel.SecurityTokenService` vers <xref:System.IdentityModel?displayProperty=fullName>.<br />- Les classes de `Microsoft.IdentityModel.Threading` ont été déplacées vers <xref:System.IdentityModel?displayProperty=fullName>.<br />- Les classes `ExceptionMapper` et `MruSecurityTokenCache` ne sont pas implémentées.|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=fullName>|- Les interfaces `IClaimsPrincipal` et `IClaimsIdentity` ne sont pas implémentées dans WIF 4.5. Désormais, <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> et <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> sont les classes de base à partir desquelles sont dérivées la plupart des classes d’identité et des classes principales .NET. Dans WIF 4.5, les classes principales et les classes d’identité de revendications spécialisées comme `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` et `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` ne sont donc pas nécessaires. Utilisez <xref:System.Security.Principal.WindowsPrincipal?displayProperty=fullName> et <xref:System.Security.Principal.WindowsIdentity?displayProperty=fullName> à la place. Il en va de même pour les autres classes principales et classes d’identité de revendications spécialisées de WIF 3.5.<br />- La classe `Microsoft.IdentityModel.Claims.ClaimsCollection` n’est pas implémentée dans WIF 4.5. Les collections de revendications sont exposées en tant que collections énumérables de type <xref:System.Security.Claims.Claim?displayProperty=fullName>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> et <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> fournissent des méthodes qui prennent entièrement en charge LINQ.|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=fullName>|Certains éléments et classes ont subi des changements de noms, et certains ont été supprimés dans WIF 4.5. Par exemple, `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` est désormais <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=fullName>.|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=fullName>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=fullName>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=fullName>|-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Non implémenté dans WIF 4.5|Dans WIF 3.5, classes contenues pour prendre en charge CardSpace. Non implémenté dans WIF 4.5.|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|Réparti entre les espaces de noms <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> et <xref:System.ServiceModel.Security?displayProperty=fullName>.|Les classes qui représentent les artefacts WS-Trust se trouvent dans l’espace de noms <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> (par exemple, la classe <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>). Les classes qui représentent les contrats de service WCF, les hôtes de service et les canaux qui permettent à un service WCF de communiquer à l’aide du protocole WS-Trust, se trouvent dans l’espace de noms <xref:System.ServiceModel.Security?displayProperty=fullName> (par exemple, la classe <xref:System.ServiceModel.Security.WSTrustServiceHost>).|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Non implémenté dans WIF 4.5|-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Non implémenté dans WIF 4.5|Classes contenues qui représentent des constantes de chiffrement XML dans WIF 3.5. Ces constantes ne sont pas implémentées dans WIF 4.5.|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=fullName>|La classe `EnvelopingSignature` et les classes qui représentent des constantes ne sont pas implémentées.|  
|`Microsoft.IdentityModel.SecurityTokenService`|Réparti entre les espaces de noms <xref:System.IdentityModel?displayProperty=fullName>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> et <xref:System.IdentityModel.Tokens?displayProperty=fullName>.|-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=fullName>|-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=fullName>|-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>|Les classes qui fournissent la configuration pour les scénarios passifs (WS-Federation) ont été en grande partie déplacées vers <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>. Toutefois, certaines de ces classes se trouvent dans <xref:System.IdentityModel.Services?displayProperty=fullName>.|  
|`Microsoft.IdentityModel.Web.Controls`|Non implémenté dans WIF 4.5|Les classes de `Microsoft.IdentityModel.Web.Controls` implémentaient le contrôle des connexions passives fédérées, qui n’existe pas dans WIF 4.5.|  
|`Microsoft.IdentityModel.WindowsTokenService`|Non implémenté dans WIF 4.5|-|  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)   
 [Recommandations sur la migration d’une application générée à l’aide de WIF 3.5 à WIF 4.5](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)

