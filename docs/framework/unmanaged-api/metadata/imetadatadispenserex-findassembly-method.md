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
ms.openlocfilehash: 7a70d1e2b3636a405fe28b84c2e76dd7264df4f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="f41ea-102">IMetaDataDispenserEx::FindAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="f41ea-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="f41ea-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="f41ea-103">This method is not implemented.</span></span> <span data-ttu-id="f41ea-104">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="f41ea-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f41ea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f41ea-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f41ea-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f41ea-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="f41ea-107">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="f41ea-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="f41ea-108">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="f41ea-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="f41ea-109">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="f41ea-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="f41ea-110">[in] L’assembly à rechercher.</span><span class="sxs-lookup"><span data-stu-id="f41ea-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="f41ea-111">[out] Le nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f41ea-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f41ea-112">[in] La taille, en octets, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="f41ea-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="f41ea-113">[out] Le nombre de caractères réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="f41ea-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f41ea-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f41ea-114">Requirements</span></span>  
 <span data-ttu-id="f41ea-115">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f41ea-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f41ea-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f41ea-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f41ea-117">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f41ea-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f41ea-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f41ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41ea-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f41ea-119">See Also</span></span>  
 [<span data-ttu-id="f41ea-120">IMetaDataDispenserEx (Interface)</span><span class="sxs-lookup"><span data-stu-id="f41ea-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="f41ea-121">IMetaDataDispenser (Interface)</span><span class="sxs-lookup"><span data-stu-id="f41ea-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
