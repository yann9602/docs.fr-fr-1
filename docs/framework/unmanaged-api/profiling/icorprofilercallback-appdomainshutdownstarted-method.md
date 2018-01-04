---
title: "ICorProfilerCallback::AppDomainShutdownStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14e515ae13e0a445580dabcdfa30253da94fd216
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="07d46-102">ICorProfilerCallback::AppDomainShutdownStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="07d46-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="07d46-103">Notifie le profileur qu’un domaine d’application est en cours de déchargement d’un processus.</span><span class="sxs-lookup"><span data-stu-id="07d46-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07d46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07d46-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07d46-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="07d46-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="07d46-106">[in] Identifie le domaine dans lequel sont stockés les assemblys de l’application.</span><span class="sxs-lookup"><span data-stu-id="07d46-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07d46-107">Notes</span><span class="sxs-lookup"><span data-stu-id="07d46-107">Remarks</span></span>  
 <span data-ttu-id="07d46-108">La valeur de `appDomainId` n’est pas valide pour toute demande d’informations après le `AppDomainShutdownStarted` retours de méthode, il s’agit permet du profileur d’obtenir des informations sur ce domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="07d46-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07d46-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="07d46-109">Requirements</span></span>  
 <span data-ttu-id="07d46-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07d46-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07d46-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07d46-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07d46-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07d46-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07d46-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07d46-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d46-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07d46-114">See Also</span></span>  
 [<span data-ttu-id="07d46-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="07d46-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
