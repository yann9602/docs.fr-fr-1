---
title: "ICorProfilerInfo2::GetThreadAppDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetThreadAppDomain
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c6e596a4610052d7586978a4e770d5df60b38ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="92802-102">ICorProfilerInfo2::GetThreadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="92802-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="92802-103">Obtient l’ID du domaine d’application dans lequel le thread spécifié est en cours d’exécution code.</span><span class="sxs-lookup"><span data-stu-id="92802-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92802-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92802-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92802-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92802-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="92802-106">[in] ID spécifiant le thread.</span><span class="sxs-lookup"><span data-stu-id="92802-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="92802-107">[out] Pointeur vers l’ID du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="92802-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92802-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="92802-108">Requirements</span></span>  
 <span data-ttu-id="92802-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92802-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92802-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92802-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92802-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92802-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92802-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92802-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92802-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92802-113">See Also</span></span>  
 [<span data-ttu-id="92802-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="92802-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="92802-115">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="92802-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
