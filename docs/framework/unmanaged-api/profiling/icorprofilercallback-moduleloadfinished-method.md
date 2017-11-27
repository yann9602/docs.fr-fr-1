---
title: "ICorProfilerCallback::ModuleLoadFinished, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22533187da02d34ac2990f351b13bd892a760620
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="edbc4-102">ICorProfilerCallback::ModuleLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="edbc4-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="edbc4-103">Notifie le profileur qu’un module a été chargé.</span><span class="sxs-lookup"><span data-stu-id="edbc4-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edbc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edbc4-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edbc4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="edbc4-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="edbc4-106">[in] L’ID du module qui a terminé son chargement.</span><span class="sxs-lookup"><span data-stu-id="edbc4-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="edbc4-107">[in] HRESULT qui indique si le module a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="edbc4-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edbc4-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="edbc4-108">Remarks</span></span>  
 <span data-ttu-id="edbc4-109">La valeur de `moduleId` n’est pas valide pour une demande d’informations jusqu'à ce que le `ModuleLoadFinished` méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="edbc4-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="edbc4-110">Certaines parties du chargement du module peuvent continuer après le `ModuleLoadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="edbc4-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="edbc4-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="edbc4-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="edbc4-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du chargement du module a réussi.</span><span class="sxs-lookup"><span data-stu-id="edbc4-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edbc4-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="edbc4-113">Requirements</span></span>  
 <span data-ttu-id="edbc4-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edbc4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edbc4-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="edbc4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="edbc4-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edbc4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edbc4-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edbc4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbc4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edbc4-118">See Also</span></span>  
 [<span data-ttu-id="edbc4-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="edbc4-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="edbc4-120">ModuleLoadStarted (méthode)</span><span class="sxs-lookup"><span data-stu-id="edbc4-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
