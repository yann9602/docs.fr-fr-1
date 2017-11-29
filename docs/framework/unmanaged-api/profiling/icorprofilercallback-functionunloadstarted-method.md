---
title: "ICorProfilerCallback::FunctionUnloadStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.FunctionUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: efd08eedf6812a46a46135eaa6f0089257f0a209
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="1b693-102">ICorProfilerCallback::FunctionUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="1b693-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="1b693-103">Notifie le profileur que le runtime a commencé à décharger une fonction.</span><span class="sxs-lookup"><span data-stu-id="1b693-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b693-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b693-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b693-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b693-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="1b693-106">[in] L’ID de la fonction qui est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="1b693-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b693-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1b693-107">Remarks</span></span>  
 <span data-ttu-id="1b693-108">La valeur de le `functionId` paramètre n’est plus valide une fois que cette méthode est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="1b693-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b693-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1b693-109">Requirements</span></span>  
 <span data-ttu-id="1b693-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b693-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b693-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b693-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b693-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b693-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b693-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b693-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b693-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b693-114">See Also</span></span>  
 [<span data-ttu-id="1b693-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1b693-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
