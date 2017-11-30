---
title: "ICorProfilerFunctionControl::SetILFunctionBody, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9469435186a5aef130ca4ebef27a4613afeb921c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="85a41-102">ICorProfilerFunctionControl::SetILFunctionBody, méthode</span><span class="sxs-lookup"><span data-stu-id="85a41-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="85a41-103">Remplace le corps Common Intermediate Language (CIL) de la méthode.</span><span class="sxs-lookup"><span data-stu-id="85a41-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85a41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85a41-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85a41-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85a41-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="85a41-106">[in] La taille totale du nouveau CIL, y compris l'en-tête et toutes structures intervenant après le corps.</span><span class="sxs-lookup"><span data-stu-id="85a41-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="85a41-107">[in] Un pointeur vers le nouvel en-tête de CIL.</span><span class="sxs-lookup"><span data-stu-id="85a41-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85a41-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="85a41-108">Return Value</span></span>  
 <span data-ttu-id="85a41-109">Cette méthode retourne les HRESULT spécifiques suivants.</span><span class="sxs-lookup"><span data-stu-id="85a41-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="85a41-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85a41-110">HRESULT</span></span>|<span data-ttu-id="85a41-111">Description</span><span class="sxs-lookup"><span data-stu-id="85a41-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85a41-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="85a41-112">S_OK</span></span>|<span data-ttu-id="85a41-113">Le remplacement a été correctement effectué.</span><span class="sxs-lookup"><span data-stu-id="85a41-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85a41-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="85a41-114">Remarks</span></span>  
 <span data-ttu-id="85a41-115">Contrairement à la [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) (méthode), la `SetILFunctionBody` méthode gère la mémoire requise pour le nouveau corps de CIL.</span><span class="sxs-lookup"><span data-stu-id="85a41-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="85a41-116">Cela signifie que le corps de CIL fourni par le profileur n’a pas à allouer à l’aide de la [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface ou dans une plage particulière.</span><span class="sxs-lookup"><span data-stu-id="85a41-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="85a41-117">Il peut être alloué sur n'importe quel segment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="85a41-117">It can be allocated on any heap.</span></span> <span data-ttu-id="85a41-118">Le profileur peut libérer la mémoire utilisée pour son corps CIL après `SetILFunctionBody` retourne.</span><span class="sxs-lookup"><span data-stu-id="85a41-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85a41-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="85a41-119">Requirements</span></span>  
 <span data-ttu-id="85a41-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85a41-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85a41-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85a41-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85a41-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85a41-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85a41-123">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85a41-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a41-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85a41-124">See Also</span></span>  
 [<span data-ttu-id="85a41-125">ICorProfilerFunctionControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="85a41-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
