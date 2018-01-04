---
title: "IMetaDataDispenserEx::FindAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f125008e4ae5b7f2abbe6d467b486b962700d42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="c1892-102">IMetaDataDispenserEx::FindAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="c1892-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="c1892-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="c1892-103">This method is not implemented.</span></span> <span data-ttu-id="c1892-104">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c1892-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1892-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1892-105">Syntax</span></span>  
  
```  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1892-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1892-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="c1892-107">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="c1892-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="c1892-108">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="c1892-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="c1892-109">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="c1892-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="c1892-110">[in] L’assembly à rechercher.</span><span class="sxs-lookup"><span data-stu-id="c1892-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="c1892-111">[out] Le nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c1892-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c1892-112">[in] La taille, en octets, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="c1892-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="c1892-113">[out] Le nombre de caractères réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="c1892-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1892-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1892-114">Requirements</span></span>  
 <span data-ttu-id="c1892-115">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1892-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1892-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1892-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1892-117">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1892-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1892-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1892-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1892-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1892-119">See Also</span></span>  
 [<span data-ttu-id="c1892-120">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="c1892-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="c1892-121">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="c1892-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
