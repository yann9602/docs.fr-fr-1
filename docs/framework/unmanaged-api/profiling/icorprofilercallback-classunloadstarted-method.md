---
title: "ICorProfilerCallback::ClassUnloadStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 994fe840f728b244e5a6e6c83c03340961c30413
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="da18e-102">ICorProfilerCallback::ClassUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="da18e-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="da18e-103">Notifie le profileur qu’une classe est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="da18e-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da18e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da18e-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da18e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da18e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="da18e-106">[in] Identifie la classe qui est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="da18e-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da18e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="da18e-107">Remarks</span></span>  
 <span data-ttu-id="da18e-108">La valeur de `classId` n’est pas valide pour une demande d’informations après le `ClassUnloadStarted` retours de méthode, il s’agit permet du profileur d’obtenir des informations sur cette classe.</span><span class="sxs-lookup"><span data-stu-id="da18e-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da18e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="da18e-109">Requirements</span></span>  
 <span data-ttu-id="da18e-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da18e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da18e-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="da18e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="da18e-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da18e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da18e-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da18e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da18e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da18e-114">See Also</span></span>  
 [<span data-ttu-id="da18e-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="da18e-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="da18e-116">ClassUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="da18e-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
