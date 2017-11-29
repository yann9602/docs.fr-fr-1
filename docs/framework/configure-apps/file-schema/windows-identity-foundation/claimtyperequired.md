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
ms.openlocfilehash: 89d42cba78eb9758d8b3491fd1bd3b25ef168f9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="37ec1-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="37ec1-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="37ec1-103">Spécifie le jeu de revendications requises pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="37ec1-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="37ec1-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="37ec1-104">\<system.identityModel></span></span>  
<span data-ttu-id="37ec1-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37ec1-105">\<identityConfiguration></span></span>  
<span data-ttu-id="37ec1-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="37ec1-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ec1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37ec1-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37ec1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="37ec1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="37ec1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="37ec1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37ec1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="37ec1-110">Attributes</span></span>  
 <span data-ttu-id="37ec1-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="37ec1-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="37ec1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="37ec1-112">Child Elements</span></span>  
  
|<span data-ttu-id="37ec1-113">Élément</span><span class="sxs-lookup"><span data-stu-id="37ec1-113">Element</span></span>|<span data-ttu-id="37ec1-114">Description</span><span class="sxs-lookup"><span data-stu-id="37ec1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37ec1-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="37ec1-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="37ec1-116">Spécifie une seule revendication facultative ou obligatoire pour les jetons de sécurité entrants.</span><span class="sxs-lookup"><span data-stu-id="37ec1-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37ec1-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="37ec1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="37ec1-118">Élément</span><span class="sxs-lookup"><span data-stu-id="37ec1-118">Element</span></span>|<span data-ttu-id="37ec1-119">Description</span><span class="sxs-lookup"><span data-stu-id="37ec1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37ec1-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37ec1-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="37ec1-121">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="37ec1-121">Specifies service-level identity settings.</span></span>|
