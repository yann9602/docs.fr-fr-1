---
title: "ICorProfilerInfo::GetILFunctionBodyAllocator, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBodyAllocator
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45a50fc39f2df9d4998f8490ff4382c84c5aa9bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="2a371-102">ICorProfilerInfo::GetILFunctionBodyAllocator, méthode</span><span class="sxs-lookup"><span data-stu-id="2a371-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="2a371-103">Obtient une interface qui fournit une méthode pour allouer de mémoire à utiliser pour permuter le corps d’une méthode dans le code Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="2a371-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a371-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a371-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a371-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2a371-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2a371-106">[in] L’ID du module dans lequel réside la méthode.</span><span class="sxs-lookup"><span data-stu-id="2a371-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="2a371-107">[out] Un pointeur vers un [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface qui fournit une méthode pour allouer la mémoire.</span><span class="sxs-lookup"><span data-stu-id="2a371-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a371-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="2a371-108">Remarks</span></span>  
 <span data-ttu-id="2a371-109">Un corps de méthode dans du code MSIL doit être localisé comme une adresse virtuelle relative (RVA), relatif au module chargé, ce qui signifie qu’il suit le module de 4 Go.</span><span class="sxs-lookup"><span data-stu-id="2a371-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="2a371-110">Pour faciliter l’utilisation d’un outil permuter le corps d’une méthode, le `GetILFunctionBodyAllocator` méthode garantit que la mémoire est allouée dans cette plage.</span><span class="sxs-lookup"><span data-stu-id="2a371-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a371-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2a371-111">Requirements</span></span>  
 <span data-ttu-id="2a371-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a371-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a371-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a371-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a371-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a371-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a371-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a371-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a371-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a371-116">See Also</span></span>  
 [<span data-ttu-id="2a371-117">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="2a371-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
