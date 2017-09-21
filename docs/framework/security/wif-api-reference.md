---
title: "Référence de l’API WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: 4
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ef439ff502fc39074d36f63d139fd23e42471d42
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="wif-api-reference"></a>Référence de l’API WIF
Les classes WIF (Windows Identity Foundation) sont réparties dans les assemblys suivants : `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) et `System.ServiceModel` (System.ServiceModel.dll). Cette rubrique fournit des liens vers les espaces de noms WIF et une brève explication des classes contenues dans chaque espace de noms.  
  
> [!IMPORTANT]
>  Les espaces de noms `System.IdentityModel` suivants contiennent des classes qui implémentent le modèle d’identité basé sur des revendications WCF : <xref:System.IdentityModel.Claims?displayProperty=fullName>, <xref:System.IdentityModel.Policy?displayProperty=fullName> et <xref:System.IdentityModel.Selectors?displayProperty=fullName>. À compter de .NET Framework 4.5, le modèle d’identité basée sur les revendications WCF est remplacé par WIF. Vous ne devez pas utiliser les classes de ces trois espaces de noms quand vous créez des solutions basées sur WIF.  
  
 <xref:System.IdentityModel?displayProperty=fullName>  
 Contient des classes qui représentent des transformations de cookies, des services d’émission de jeton de sécurité et des lecteurs de dictionnaires XML spécifiques.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=fullName>  
 Contient des classes qui spécifient la configuration pour les applications et services créés à l’aide de WIF. Les classes de cet espace de noms représentent les paramètres sous l’élément [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).  
  
 <xref:System.IdentityModel.Metadata?displayProperty=fullName>  
 Contient des classes qui représentent des éléments dans un document de métadonnées de fédération.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>  
 Contient des classes qui représentent des artefacts WS-Trust.  
  
 <xref:System.IdentityModel.Services?displayProperty=fullName>  
 Contient des classes utilisées dans des scénarios passifs (WS-Federation). Contient également des classes qui représentent les paramètres sous l’élément [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). Les paramètres sous cet élément configurent WS-Federation pour les applications. L’espace de noms `System.IdentityModel.Services.Configuration` contient la plupart des classes utilisées pour configurer WS-Federation.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>  
 Contient des classes qui spécifient la configuration pour les applications WIF utilisant le protocole WS-Federation. Les classes de cet espace de noms représentent les paramètres sous l’élément [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). L’espace de noms `System.IdentityModel.Services` contient aussi des classes qui sont utilisées pour configurer WS-Federation.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=fullName>  
 Contient des gestionnaires de jetons de sécurité spécifiques pour les scénarios avec batterie de serveurs web.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=fullName>  
 Contient des classes qui représentent des jetons de sécurité, des gestionnaires de jetons de sécurité et d’autres artefacts de jetons de sécurité.  
  
 <xref:System.Security.Claims?displayProperty=fullName>  
 Contient des classes qui représentent des revendications, des identités basées sur les revendications, des principaux basés sur les revendications et d’autres artefacts de modèles d’identité basée sur les revendications.  
  
 <xref:System.ServiceModel.Security?displayProperty=fullName>  
 Contient des classes qui représentent des contrats, canaux et hôtes de service WCF, ainsi que d’autres artefacts utilisés dans des scénarios actifs (WS-Trust). Cet espace de noms contient également des classes propres à WCF qui ne sont pas utilisées par WIF.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la configuration de WIF](../../../docs/framework/security/wif-configuration-reference.md)   
 [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)

