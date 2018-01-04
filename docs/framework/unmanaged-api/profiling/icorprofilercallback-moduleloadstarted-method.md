---
title: "ICorProfilerCallback::ModuleLoadStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f88b2a287eef0bf3fe8edeba4b76a3b3a1ce4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="f2f27-102">ICorProfilerCallback::ModuleLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="f2f27-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="f2f27-103">Notifie le profileur qu’un module est chargé.</span><span class="sxs-lookup"><span data-stu-id="f2f27-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2f27-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2f27-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2f27-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f2f27-106">[in] L’ID du module chargé.</span><span class="sxs-lookup"><span data-stu-id="f2f27-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2f27-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f2f27-107">Remarks</span></span>  
 <span data-ttu-id="f2f27-108">La valeur de `moduleId` n’est pas valide pour une demande d’informations jusqu'à ce que le [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="f2f27-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f27-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f2f27-109">Requirements</span></span>  
 <span data-ttu-id="f2f27-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2f27-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f27-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2f27-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2f27-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2f27-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2f27-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f27-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f27-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2f27-114">See Also</span></span>  
 [<span data-ttu-id="f2f27-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f2f27-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
