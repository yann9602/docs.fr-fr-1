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
ms.openlocfilehash: c4ee8833578b082f25c427b13d77072d1954197f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="18f0b-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="18f0b-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="18f0b-103">Spécifie une seule revendication facultative ou obligatoire pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="18f0b-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="18f0b-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="18f0b-104">\<system.identityModel></span></span>  
<span data-ttu-id="18f0b-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="18f0b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="18f0b-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="18f0b-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="18f0b-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="18f0b-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f0b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18f0b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18f0b-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="18f0b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="18f0b-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="18f0b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18f0b-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="18f0b-111">Attributes</span></span>  
  
|<span data-ttu-id="18f0b-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="18f0b-112">Attribute</span></span>|<span data-ttu-id="18f0b-113">Description</span><span class="sxs-lookup"><span data-stu-id="18f0b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18f0b-114">type</span><span class="sxs-lookup"><span data-stu-id="18f0b-114">type</span></span>|<span data-ttu-id="18f0b-115">Type de revendication.</span><span class="sxs-lookup"><span data-stu-id="18f0b-115">The claim type.</span></span> <span data-ttu-id="18f0b-116">En général un URI.</span><span class="sxs-lookup"><span data-stu-id="18f0b-116">Typically a URI.</span></span> <span data-ttu-id="18f0b-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="18f0b-117">Required.</span></span>|  
|<span data-ttu-id="18f0b-118">facultatifs</span><span class="sxs-lookup"><span data-stu-id="18f0b-118">optional</span></span>|<span data-ttu-id="18f0b-119">Valeur booléenne qui spécifie si le type de revendication est facultatif.</span><span class="sxs-lookup"><span data-stu-id="18f0b-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="18f0b-120">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="18f0b-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18f0b-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="18f0b-121">Child Elements</span></span>  
 <span data-ttu-id="18f0b-122">None</span><span class="sxs-lookup"><span data-stu-id="18f0b-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18f0b-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="18f0b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="18f0b-124">Élément</span><span class="sxs-lookup"><span data-stu-id="18f0b-124">Element</span></span>|<span data-ttu-id="18f0b-125">Description</span><span class="sxs-lookup"><span data-stu-id="18f0b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18f0b-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="18f0b-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="18f0b-127">Spécifie le jeu de revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="18f0b-127">Specifies the set of required claims for incoming security tokens.</span></span>|
