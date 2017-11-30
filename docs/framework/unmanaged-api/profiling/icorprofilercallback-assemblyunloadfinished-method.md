---
title: "ICorProfilerCallback::AssemblyUnloadFinished, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 144f7af59afbb403d9ec1894f06c5c028b767416
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="f49c0-102">ICorProfilerCallback::AssemblyUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="f49c0-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="f49c0-103">Informe le profileur qu’un assembly a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="f49c0-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f49c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f49c0-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f49c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f49c0-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="f49c0-106">[in] Identifie l’assembly qui est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="f49c0-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f49c0-107">[in] HRESULT qui indique si l’assembly a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="f49c0-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f49c0-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="f49c0-108">Remarks</span></span>  
 <span data-ttu-id="f49c0-109">La valeur de `assemblyId` n’est pas valide pour une demande d’informations après le [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) retourne de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f49c0-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="f49c0-110">Certaines parties du déchargement de l’assembly peuvent continuer après le `AssemblyUnloadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="f49c0-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="f49c0-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="f49c0-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f49c0-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement de l’assembly a réussi.</span><span class="sxs-lookup"><span data-stu-id="f49c0-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f49c0-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f49c0-113">Requirements</span></span>  
 <span data-ttu-id="f49c0-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f49c0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f49c0-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f49c0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f49c0-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f49c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f49c0-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f49c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49c0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f49c0-118">See Also</span></span>  
 [<span data-ttu-id="f49c0-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f49c0-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
