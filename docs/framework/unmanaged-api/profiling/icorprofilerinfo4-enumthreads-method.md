---
title: "ICorProfilerInfo4::EnumThreads, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumThreads
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 20022a3b7353c0e43aaa44e368c06cd79906956e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="35c69-102">ICorProfilerInfo4::EnumThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="35c69-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="35c69-103">Retourne un énumérateur qui fournit des méthodes pour boucler séquentiellement dans la collection de tous les threads managés dans le processus profilé.</span><span class="sxs-lookup"><span data-stu-id="35c69-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35c69-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35c69-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35c69-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="35c69-106">[out] Un pointeur vers un [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="35c69-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35c69-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="35c69-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35c69-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="35c69-108">Requirements</span></span>  
 <span data-ttu-id="35c69-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35c69-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35c69-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="35c69-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35c69-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35c69-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35c69-112">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35c69-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c69-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35c69-113">See Also</span></span>  
 [<span data-ttu-id="35c69-114">ICorProfilerThreadEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="35c69-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="35c69-115">Icorprofilerinfo4, Interface</span><span class="sxs-lookup"><span data-stu-id="35c69-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="35c69-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="35c69-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="35c69-117">Profilage</span><span class="sxs-lookup"><span data-stu-id="35c69-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
