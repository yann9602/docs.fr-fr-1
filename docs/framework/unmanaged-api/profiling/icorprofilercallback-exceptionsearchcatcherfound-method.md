---
title: "ICorProfilerCallback::ExceptionSearchCatcherFound, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchCatcherFound
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc226b6102c50b118a4b13f9cd25700dd1ca7301
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="5548a-102">ICorProfilerCallback::ExceptionSearchCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="5548a-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="5548a-103">Notifie le profileur que la phase de recherche de la gestion des exceptions a trouvé un gestionnaire pour l’exception qui a été levée.</span><span class="sxs-lookup"><span data-stu-id="5548a-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5548a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5548a-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5548a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5548a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5548a-106">[in] L’ID de la fonction qui contient le Gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="5548a-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5548a-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5548a-107">Requirements</span></span>  
 <span data-ttu-id="5548a-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5548a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5548a-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5548a-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5548a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5548a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5548a-111">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5548a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5548a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5548a-112">See Also</span></span>  
 [<span data-ttu-id="5548a-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="5548a-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
