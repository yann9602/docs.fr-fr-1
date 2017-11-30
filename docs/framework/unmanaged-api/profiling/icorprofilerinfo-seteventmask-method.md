---
title: "ICorProfilerInfo::SetEventMask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bb42be7f8e5722ec9924284c257e814a186564d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="5ed77-102">ICorProfilerInfo::SetEventMask, méthode</span><span class="sxs-lookup"><span data-stu-id="5ed77-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="5ed77-103">Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir une notification du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="5ed77-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ed77-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ed77-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ed77-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="5ed77-106">[en entrée] Une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="5ed77-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="5ed77-107">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="5ed77-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="5ed77-108">Les bits sont décrits dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="5ed77-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ed77-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ed77-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ed77-110">Vous devez appeler la [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthode au lieu de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="5ed77-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="5ed77-111">Bien que le `SetEventMask` méthode continue à être pris en charge, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) fournit des fonctionnalités supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="5ed77-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed77-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5ed77-112">Requirements</span></span>  
 <span data-ttu-id="5ed77-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed77-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed77-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ed77-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ed77-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ed77-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ed77-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed77-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed77-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ed77-117">See Also</span></span>  
 [<span data-ttu-id="5ed77-118">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="5ed77-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="5ed77-119">Seteventmask2, méthode</span><span class="sxs-lookup"><span data-stu-id="5ed77-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
