---
title: "ICorProfilerInfo3::EnumModules, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.EnumModules Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0215662439672aecc787530ceb68d16cc58bcc3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="81cc9-102">ICorProfilerInfo3::EnumModules, méthode</span><span class="sxs-lookup"><span data-stu-id="81cc9-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="81cc9-103">Retourne un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein d’une collection de modules managés chargés dans l’application.</span><span class="sxs-lookup"><span data-stu-id="81cc9-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81cc9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81cc9-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81cc9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="81cc9-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="81cc9-106">[out] Un pointeur vers un [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="81cc9-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81cc9-107">Notes</span><span class="sxs-lookup"><span data-stu-id="81cc9-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81cc9-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81cc9-108">Requirements</span></span>  
 <span data-ttu-id="81cc9-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81cc9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81cc9-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="81cc9-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="81cc9-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81cc9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81cc9-112">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81cc9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81cc9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81cc9-113">See Also</span></span>  
 [<span data-ttu-id="81cc9-114">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="81cc9-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="81cc9-115">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="81cc9-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="81cc9-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="81cc9-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="81cc9-117">Profilage</span><span class="sxs-lookup"><span data-stu-id="81cc9-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
