---
title: "Référence de l’API WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d7ae7ef82d12c024441d01ef420bc9366e3c589d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="wif-api-reference"></a><span data-ttu-id="f0927-102">Référence de l’API WIF</span><span class="sxs-lookup"><span data-stu-id="f0927-102">WIF API Reference</span></span>
<span data-ttu-id="f0927-103">Les classes WIF (Windows Identity Foundation) sont réparties dans les assemblys suivants : `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll) et `System.ServiceModel` (System.ServiceModel.dll).</span><span class="sxs-lookup"><span data-stu-id="f0927-103">Windows Identity Foundation (WIF) classes are split across the following assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), and `System.ServiceModel` (System.ServiceModel.dll).</span></span> <span data-ttu-id="f0927-104">Cette rubrique fournit des liens vers les espaces de noms WIF et une brève explication des classes contenues dans chaque espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f0927-104">This topic provides links to the WIF namespaces and brief explanations of the classes that each namespace contains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f0927-105">Les espaces de noms `System.IdentityModel` suivants contiennent des classes qui implémentent le modèle d’identité basé sur des revendications WCF : <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> et <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0927-105">The following `System.IdentityModel` namespaces contain classes that implement the WCF claims-based identity model: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, and <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f0927-106">À compter de .NET Framework 4.5, le modèle d’identité basée sur les revendications WCF est remplacé par WIF.</span><span class="sxs-lookup"><span data-stu-id="f0927-106">Starting with .NET Framework 4.5, the WCF claims-based identity model is superseded by WIF.</span></span> <span data-ttu-id="f0927-107">Vous ne devez pas utiliser les classes de ces trois espaces de noms quand vous créez des solutions basées sur WIF.</span><span class="sxs-lookup"><span data-stu-id="f0927-107">You should not use classes in these three namespaces when building solutions based on WIF.</span></span>  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-108">Contient des classes qui représentent des transformations de cookies, des services d’émission de jeton de sécurité et des lecteurs de dictionnaires XML spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f0927-108">Contains classes that represent cookie transforms, security token services, and specialized XML dictionary readers.</span></span>  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-109">Contient des classes qui spécifient la configuration pour les applications et services créés à l’aide de WIF.</span><span class="sxs-lookup"><span data-stu-id="f0927-109">Contains classes that provide configuration for applications and services built using the Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="f0927-110">Les classes de cet espace de noms représentent les paramètres sous l’élément [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).</span><span class="sxs-lookup"><span data-stu-id="f0927-110">The classes in this namespace represent settings under the [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-111">Contient des classes qui représentent des éléments dans un document de métadonnées de fédération.</span><span class="sxs-lookup"><span data-stu-id="f0927-111">Contains classes that represent elements in a Federation Metadata document.</span></span>  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-112">Contient des classes qui représentent des artefacts WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="f0927-112">Contains classes that represent WS-Trust artifacts.</span></span>  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-113">Contient des classes utilisées dans des scénarios passifs (WS-Federation).</span><span class="sxs-lookup"><span data-stu-id="f0927-113">Contains classes that are used in passive (WS-Federation) scenarios.</span></span> <span data-ttu-id="f0927-114">Contient également des classes qui représentent les paramètres sous l’élément [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0927-114">Also contains some classes that represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="f0927-115">Les paramètres sous cet élément configurent WS-Federation pour les applications.</span><span class="sxs-lookup"><span data-stu-id="f0927-115">Settings under this element configure WS-Federation for applications.</span></span> <span data-ttu-id="f0927-116">L’espace de noms `System.IdentityModel.Services.Configuration` contient la plupart des classes utilisées pour configurer WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="f0927-116">The `System.IdentityModel.Services.Configuration` namespace contains most of the classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-117">Contient des classes qui spécifient la configuration pour les applications WIF utilisant le protocole WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="f0927-117">Contains classes that provide configuration for WIF applications that use the WS-Federation protocol.</span></span> <span data-ttu-id="f0927-118">Les classes de cet espace de noms représentent les paramètres sous l’élément [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0927-118">The classes in this namespace represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="f0927-119">L’espace de noms `System.IdentityModel.Services` contient aussi des classes qui sont utilisées pour configurer WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="f0927-119">The `System.IdentityModel.Services` namespace also contains some classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-120">Contient des gestionnaires de jetons de sécurité spécifiques pour les scénarios avec batterie de serveurs web.</span><span class="sxs-lookup"><span data-stu-id="f0927-120">Contains specialized security token handlers for Web farm scenarios.</span></span>  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-121">Contient des classes qui représentent des jetons de sécurité, des gestionnaires de jetons de sécurité et d’autres artefacts de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f0927-121">Contains classes that represent security tokens, security token handlers, and other security token artifacts.</span></span>  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-122">Contient des classes qui représentent des revendications, des identités basées sur les revendications, des principaux basés sur les revendications et d’autres artefacts de modèles d’identité basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="f0927-122">Contains classes that represent claims, claims-based identities, claims-based principals, and other claims-based identity model artifacts.</span></span>  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 <span data-ttu-id="f0927-123">Contient des classes qui représentent des contrats, canaux et hôtes de service WCF, ainsi que d’autres artefacts utilisés dans des scénarios actifs (WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="f0927-123">Contains classes that represent WCF contracts, channels, service hosts and other artifacts that are used in active (WS-Trust) scenarios.</span></span> <span data-ttu-id="f0927-124">Cet espace de noms contient également des classes propres à WCF qui ne sont pas utilisées par WIF.</span><span class="sxs-lookup"><span data-stu-id="f0927-124">This namespace also contains classes that are specific to Windows Communication Foundation (WCF) and that are not used by WIF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0927-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0927-125">See Also</span></span>  
 [<span data-ttu-id="f0927-126">Référence de configuration de WIF</span><span class="sxs-lookup"><span data-stu-id="f0927-126">WIF Configuration Reference</span></span>](../../../docs/framework/security/wif-configuration-reference.md)  
 [<span data-ttu-id="f0927-127">Mappage des espaces de noms entre WIF 3.5 et WIF 4.5</span><span class="sxs-lookup"><span data-stu-id="f0927-127">Namespace Mapping between WIF 3.5 and WIF 4.5</span></span>](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
