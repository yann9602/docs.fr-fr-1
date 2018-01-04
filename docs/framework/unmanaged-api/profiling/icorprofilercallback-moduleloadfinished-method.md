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
ms.workload: dotnet
ms.openlocfilehash: 360c14ccdd67cb7609ffe2f9c49914fdda163389
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="c49bb-102">ICorProfilerCallback::ModuleLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="c49bb-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="c49bb-103">Notifie le profileur qu’un module a été chargé.</span><span class="sxs-lookup"><span data-stu-id="c49bb-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c49bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c49bb-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c49bb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c49bb-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c49bb-106">[in] L’ID du module qui a terminé son chargement.</span><span class="sxs-lookup"><span data-stu-id="c49bb-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c49bb-107">[in] HRESULT qui indique si le module a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="c49bb-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c49bb-108">Notes</span><span class="sxs-lookup"><span data-stu-id="c49bb-108">Remarks</span></span>  
 <span data-ttu-id="c49bb-109">La valeur de `moduleId` n’est pas valide pour une demande d’informations jusqu'à ce que le `ModuleLoadFinished` méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="c49bb-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="c49bb-110">Certaines parties du chargement du module peuvent continuer après le `ModuleLoadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="c49bb-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="c49bb-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="c49bb-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c49bb-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du chargement du module a réussi.</span><span class="sxs-lookup"><span data-stu-id="c49bb-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c49bb-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c49bb-113">Requirements</span></span>  
 <span data-ttu-id="c49bb-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c49bb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c49bb-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c49bb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c49bb-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c49bb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c49bb-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c49bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c49bb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c49bb-118">See Also</span></span>  
 [<span data-ttu-id="c49bb-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c49bb-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c49bb-120">ModuleLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="c49bb-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
