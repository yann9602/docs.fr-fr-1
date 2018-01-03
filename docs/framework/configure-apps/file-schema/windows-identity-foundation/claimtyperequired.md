---
title: '&lt;claimTypeRequired&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 491277e39b29d7c3e0a0d69ec8745b2c6718a91e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="efe04-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="efe04-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="efe04-103">Spécifie le jeu de revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="efe04-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="efe04-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="efe04-104">\<system.identityModel></span></span>  
<span data-ttu-id="efe04-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="efe04-105">\<identityConfiguration></span></span>  
<span data-ttu-id="efe04-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="efe04-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe04-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efe04-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efe04-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="efe04-108">Attributes and Elements</span></span>  
 <span data-ttu-id="efe04-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="efe04-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efe04-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="efe04-110">Attributes</span></span>  
 <span data-ttu-id="efe04-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="efe04-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="efe04-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="efe04-112">Child Elements</span></span>  
  
|<span data-ttu-id="efe04-113">Élément</span><span class="sxs-lookup"><span data-stu-id="efe04-113">Element</span></span>|<span data-ttu-id="efe04-114">Description</span><span class="sxs-lookup"><span data-stu-id="efe04-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efe04-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="efe04-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="efe04-116">Spécifie une seule revendication facultative ou obligatoire pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="efe04-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efe04-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="efe04-117">Parent Elements</span></span>  
  
|<span data-ttu-id="efe04-118">Élément</span><span class="sxs-lookup"><span data-stu-id="efe04-118">Element</span></span>|<span data-ttu-id="efe04-119">Description</span><span class="sxs-lookup"><span data-stu-id="efe04-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efe04-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="efe04-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="efe04-121">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="efe04-121">Specifies service-level identity settings.</span></span>|
