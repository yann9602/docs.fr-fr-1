---
title: "ICorProfilerCallback::ClassLoadStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22b6d4ca72b0ee95af1c7baae63223cb09435971
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="09fbe-102">ICorProfilerCallback::ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="09fbe-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="09fbe-103">Notifie le profileur qu’une classe est chargée.</span><span class="sxs-lookup"><span data-stu-id="09fbe-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09fbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09fbe-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09fbe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09fbe-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="09fbe-106">[in] Identifie la classe qui est chargée.</span><span class="sxs-lookup"><span data-stu-id="09fbe-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09fbe-107">Notes</span><span class="sxs-lookup"><span data-stu-id="09fbe-107">Remarks</span></span>  
 <span data-ttu-id="09fbe-108">La valeur de `classId` n’est pas valide pour une demande d’informations jusqu'à ce que le [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="09fbe-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09fbe-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="09fbe-109">Requirements</span></span>  
 <span data-ttu-id="09fbe-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09fbe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09fbe-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09fbe-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09fbe-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09fbe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09fbe-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09fbe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09fbe-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09fbe-114">See Also</span></span>  
 [<span data-ttu-id="09fbe-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="09fbe-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
