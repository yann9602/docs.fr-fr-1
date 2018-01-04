---
title: "ICorProfilerCallback::AssemblyUnloadStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9984cff1d3c4013d66bc9eb7dbe5dbe7b61d2ba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="2ad22-102">ICorProfilerCallback::AssemblyUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="2ad22-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="2ad22-103">Notifie le profileur qu’un assembly est déchargé.</span><span class="sxs-lookup"><span data-stu-id="2ad22-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ad22-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ad22-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ad22-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="2ad22-106">[in] Identifie l’assembly qui est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="2ad22-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ad22-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2ad22-107">Remarks</span></span>  
 <span data-ttu-id="2ad22-108">La valeur de `assemblyId` n’est pas valide pour une demande d’informations après le `AssemblyUnloadStarted` retours de méthode, il s’agit permet du profileur d’obtenir des informations sur cet assembly.</span><span class="sxs-lookup"><span data-stu-id="2ad22-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ad22-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ad22-109">Requirements</span></span>  
 <span data-ttu-id="2ad22-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ad22-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ad22-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2ad22-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ad22-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ad22-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ad22-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ad22-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad22-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ad22-114">See Also</span></span>  
 [<span data-ttu-id="2ad22-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="2ad22-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="2ad22-116">AssemblyUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="2ad22-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
