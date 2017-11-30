---
title: '&lt;tokenReplayDetection&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f95d200f74621a40d2987acf68bc554df8d17ab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="9276e-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="9276e-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="9276e-103">Active la détection de relecture de jetons et spécifie le délai d’expiration pour les jetons.</span><span class="sxs-lookup"><span data-stu-id="9276e-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="9276e-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="9276e-104">\<system.identityModel></span></span>  
<span data-ttu-id="9276e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9276e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9276e-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="9276e-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9276e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9276e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="9276e-108">Type</span><span class="sxs-lookup"><span data-stu-id="9276e-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9276e-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9276e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9276e-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9276e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9276e-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="9276e-111">Attributes</span></span>  
  
|<span data-ttu-id="9276e-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="9276e-112">Attribute</span></span>|<span data-ttu-id="9276e-113">Description</span><span class="sxs-lookup"><span data-stu-id="9276e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9276e-114">enabled</span><span class="sxs-lookup"><span data-stu-id="9276e-114">enabled</span></span>|<span data-ttu-id="9276e-115">Une valeur qui spécifie si la détection de relecture de jetons est activée ; « true » pour activer le jeton de la détection de relecture.</span><span class="sxs-lookup"><span data-stu-id="9276e-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="9276e-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="9276e-116">expirationPeriod</span></span>|<span data-ttu-id="9276e-117">Un <xref:System.TimeSpan> qui spécifie la durée maximale avant un élément est considéré comme expiré et supprimé du cache.</span><span class="sxs-lookup"><span data-stu-id="9276e-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="9276e-118">Pour plus d’informations sur la façon de spécifier <xref:System.TimeSpan> valeurs, consultez [valeurs Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="9276e-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9276e-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9276e-119">Child Elements</span></span>  
 <span data-ttu-id="9276e-120">None</span><span class="sxs-lookup"><span data-stu-id="9276e-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9276e-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9276e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9276e-122">Élément</span><span class="sxs-lookup"><span data-stu-id="9276e-122">Element</span></span>|<span data-ttu-id="9276e-123">Description</span><span class="sxs-lookup"><span data-stu-id="9276e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9276e-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9276e-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="9276e-125">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="9276e-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="9276e-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9276e-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="9276e-127">Fournit des gestionnaires de jetons de configuration pour une collection de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9276e-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9276e-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="9276e-128">Remarks</span></span>  
 <span data-ttu-id="9276e-129">A `<tokenReplayDetection>` élément peut être spécifié au niveau du service sous le `<identityConfiguration>` élément ou sur le niveau de regroupement de gestionnaire de jetons de sécurité sous le `<securityTokenHandlerConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="9276e-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="9276e-130">Paramètres sur une collection de gestionnaire de jetons remplacent celles spécifiées sur le service.</span><span class="sxs-lookup"><span data-stu-id="9276e-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="9276e-131">Le type du cache de relecture de jetons est spécifié par le [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) élément.</span><span class="sxs-lookup"><span data-stu-id="9276e-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
