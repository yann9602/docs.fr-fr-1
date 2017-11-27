---
title: "ICorProfilerCallback::ModuleUnloadFinished, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dc97a4173e384622fefa7de528a9725b68923ff2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="c939a-102">ICorProfilerCallback::ModuleUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="c939a-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="c939a-103">Notifie le profileur qu’un module a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="c939a-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c939a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c939a-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c939a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c939a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c939a-106">[in] L’ID du module qui a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="c939a-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c939a-107">[in] HRESULT qui indique si le module a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="c939a-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c939a-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="c939a-108">Remarks</span></span>  
 <span data-ttu-id="c939a-109">La valeur de `moduleId` n’est pas valide pour une demande d’informations après le [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) retourne de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c939a-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="c939a-110">Certaines parties du déchargement de la classe peuvent continuer après le `ModuleUnloadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="c939a-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="c939a-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="c939a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c939a-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement du module a réussi.</span><span class="sxs-lookup"><span data-stu-id="c939a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c939a-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c939a-113">Requirements</span></span>  
 <span data-ttu-id="c939a-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c939a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c939a-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c939a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c939a-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c939a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c939a-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c939a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c939a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c939a-118">See Also</span></span>  
 [<span data-ttu-id="c939a-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c939a-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
