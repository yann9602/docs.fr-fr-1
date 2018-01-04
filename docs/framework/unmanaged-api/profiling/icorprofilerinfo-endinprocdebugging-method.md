---
title: "ICorProfilerInfo::EndInprocDebugging, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.EndInprocDebugging
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a36c557d9ab2fa661808aa2f0be942d11ea9fa61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="22bc1-102">ICorProfilerInfo::EndInprocDebugging, méthode</span><span class="sxs-lookup"><span data-stu-id="22bc1-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="22bc1-103">Arrête une session de débogage in-process.</span><span class="sxs-lookup"><span data-stu-id="22bc1-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="22bc1-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="22bc1-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22bc1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22bc1-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22bc1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="22bc1-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="22bc1-107">[in] Une valeur qui identifie la session de débogage.</span><span class="sxs-lookup"><span data-stu-id="22bc1-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="22bc1-108">Cette valeur doit être la même que celle reçue dans la [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="22bc1-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22bc1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="22bc1-109">Remarks</span></span>  
 <span data-ttu-id="22bc1-110">Vous devez appeler [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) et `EndInprocDebugging` au sein de la même méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="22bc1-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="22bc1-111">Les services de débogage CLR pris en charge limitée dans le processus de débogage dans les versions du .NET Framework 1.0 et 1.1.</span><span class="sxs-lookup"><span data-stu-id="22bc1-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="22bc1-112">Dans le processus de débogage activé un profileur d’utiliser les parties de l’inspection de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="22bc1-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="22bc1-113">Toutefois, en raison des commentaires des clients, dans le processus de débogage ont été supprimé du .NET Framework version 2.0 et remplacé par un ensemble de fonctionnalités qui sont plus adaptées à l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="22bc1-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22bc1-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="22bc1-114">Requirements</span></span>  
 <span data-ttu-id="22bc1-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22bc1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22bc1-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22bc1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22bc1-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22bc1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22bc1-118">**Version du .NET framework :** 1.0</span><span class="sxs-lookup"><span data-stu-id="22bc1-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22bc1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22bc1-119">See Also</span></span>  
 [<span data-ttu-id="22bc1-120">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="22bc1-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
