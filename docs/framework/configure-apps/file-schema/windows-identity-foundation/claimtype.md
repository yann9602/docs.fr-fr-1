---
title: '&lt;claimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ae572ff3a8a2335a4259bdce2af5f6922fb0596f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="4b26a-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="4b26a-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="4b26a-103">Spécifie une seule revendication facultative ou obligatoire pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="4b26a-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="4b26a-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="4b26a-104">\<system.identityModel></span></span>  
<span data-ttu-id="4b26a-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4b26a-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4b26a-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="4b26a-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="4b26a-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="4b26a-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b26a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b26a-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b26a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4b26a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4b26a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4b26a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b26a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="4b26a-111">Attributes</span></span>  
  
|<span data-ttu-id="4b26a-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="4b26a-112">Attribute</span></span>|<span data-ttu-id="4b26a-113">Description</span><span class="sxs-lookup"><span data-stu-id="4b26a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b26a-114">type</span><span class="sxs-lookup"><span data-stu-id="4b26a-114">type</span></span>|<span data-ttu-id="4b26a-115">Type de revendication.</span><span class="sxs-lookup"><span data-stu-id="4b26a-115">The claim type.</span></span> <span data-ttu-id="4b26a-116">En général un URI.</span><span class="sxs-lookup"><span data-stu-id="4b26a-116">Typically a URI.</span></span> <span data-ttu-id="4b26a-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4b26a-117">Required.</span></span>|  
|<span data-ttu-id="4b26a-118">facultatifs</span><span class="sxs-lookup"><span data-stu-id="4b26a-118">optional</span></span>|<span data-ttu-id="4b26a-119">Valeur booléenne qui spécifie si le type de revendication est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4b26a-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="4b26a-120">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4b26a-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b26a-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4b26a-121">Child Elements</span></span>  
 <span data-ttu-id="4b26a-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4b26a-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b26a-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4b26a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4b26a-124">Élément</span><span class="sxs-lookup"><span data-stu-id="4b26a-124">Element</span></span>|<span data-ttu-id="4b26a-125">Description</span><span class="sxs-lookup"><span data-stu-id="4b26a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b26a-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="4b26a-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="4b26a-127">Spécifie le jeu de revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="4b26a-127">Specifies the set of required claims for incoming security tokens.</span></span>|
