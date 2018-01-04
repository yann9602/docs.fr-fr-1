---
title: "ICorProfilerInfo::GetThreadContext, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetThreadContext
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 630236e6f20b61d4a73bcb26a61112151a8ed80c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="31750-102">ICorProfilerInfo::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="31750-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="31750-103">Obtient l’identité de contexte actuellement associée au thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="31750-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31750-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31750-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31750-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31750-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="31750-106">[in] L’ID du thread.</span><span class="sxs-lookup"><span data-stu-id="31750-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="31750-107">[out] Pointeur vers l’ID de contexte actuellement associé au thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="31750-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="31750-108">Si le thread n’a aucun contexte actuellement associé, cette fonction retournera CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="31750-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31750-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31750-109">Requirements</span></span>  
 <span data-ttu-id="31750-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31750-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31750-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31750-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31750-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31750-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31750-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31750-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31750-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31750-114">See Also</span></span>  
 [<span data-ttu-id="31750-115">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="31750-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
