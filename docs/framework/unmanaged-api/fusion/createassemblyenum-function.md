---
title: CreateAssemblyEnum, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyEnum
helpviewer_keywords: CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c229496a79b146b5dcac3d06fa3efd9237e39d3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="92163-102">CreateAssemblyEnum, fonction</span><span class="sxs-lookup"><span data-stu-id="92163-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="92163-103">Obtient un pointeur vers un [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance qui peut énumérer les objets dans l’assembly avec l’objet [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="92163-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92163-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92163-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92163-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92163-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="92163-106">[out] Pointeur vers un emplacement de mémoire qui contient l’élément demandé `IAssemblyEnum` pointeur.</span><span class="sxs-lookup"><span data-stu-id="92163-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="92163-107">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="92163-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="92163-108">`pUnkReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="92163-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="92163-109">[in] Le `IAssemblyName` de l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="92163-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="92163-110">Ce nom est utilisé pour filtrer l’énumération.</span><span class="sxs-lookup"><span data-stu-id="92163-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="92163-111">Il peut être null pour énumérer tous les assemblys dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="92163-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="92163-112">[in] Indicateurs permettant de modifier le comportement de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="92163-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="92163-113">Ce paramètre contient exactement un bit de le [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="92163-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="92163-114">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="92163-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="92163-115">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="92163-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92163-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="92163-116">Remarks</span></span>  
 <span data-ttu-id="92163-117">Le `dwFlags` paramètre contient exactement un bit de le `ASM_CACHE_FLAGS` énumération.</span><span class="sxs-lookup"><span data-stu-id="92163-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92163-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="92163-118">Requirements</span></span>  
 <span data-ttu-id="92163-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92163-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92163-120">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="92163-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="92163-121">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92163-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92163-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92163-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92163-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92163-123">See Also</span></span>  
 [<span data-ttu-id="92163-124">IAssemblyEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="92163-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [<span data-ttu-id="92163-125">IAssemblyName (Interface)</span><span class="sxs-lookup"><span data-stu-id="92163-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="92163-126">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="92163-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
