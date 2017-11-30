---
title: GetCachePath, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: GetCachePath
helpviewer_keywords: GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 924482bf34d53d3d7144c4bae93a00a8f8d2ad4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getcachepath-function"></a><span data-ttu-id="48295-102">GetCachePath, fonction</span><span class="sxs-lookup"><span data-stu-id="48295-102">GetCachePath Function</span></span>
<span data-ttu-id="48295-103">Obtient le chemin d’accès à l’assembly mis en cache, à l’aide des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="48295-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48295-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48295-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48295-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="48295-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="48295-106">[in] Un [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) valeur qui indique la source de l’assembly mis en cache.</span><span class="sxs-lookup"><span data-stu-id="48295-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="48295-107">[out] Le pointeur retourné pour le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="48295-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="48295-108">[dans, out] La longueur maximale demandée de `pwzCachePath`et au moment du retour, la longueur réelle de `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="48295-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48295-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="48295-109">Requirements</span></span>  
 <span data-ttu-id="48295-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48295-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48295-111">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="48295-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="48295-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48295-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48295-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48295-113">See Also</span></span>  
 [<span data-ttu-id="48295-114">ASM_CACHE_FLAGS (énumération)</span><span class="sxs-lookup"><span data-stu-id="48295-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [<span data-ttu-id="48295-115">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="48295-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
