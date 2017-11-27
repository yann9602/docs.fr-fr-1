---
title: "COR_PRF_SUSPEND_REASON, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SUSPEND_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SUSPEND_REASON
helpviewer_keywords: COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aef9688d3da047645d53f6fcf113153393780c8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="96294-102">COR_PRF_SUSPEND_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="96294-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="96294-103">Indique la raison pour laquelle le runtime est suspendu.</span><span class="sxs-lookup"><span data-stu-id="96294-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96294-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96294-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="96294-105">Membres</span><span class="sxs-lookup"><span data-stu-id="96294-105">Members</span></span>  
  
|<span data-ttu-id="96294-106">Membre</span><span class="sxs-lookup"><span data-stu-id="96294-106">Member</span></span>|<span data-ttu-id="96294-107">Description</span><span class="sxs-lookup"><span data-stu-id="96294-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="96294-108">L’exécution est interrompu pour une raison non spécifiée.</span><span class="sxs-lookup"><span data-stu-id="96294-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="96294-109">Le runtime est suspendu pour traiter une demande de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="96294-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="96294-110">Les rappels de collection associés au garbage ont lieu entre les [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) et [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) rappels.</span><span class="sxs-lookup"><span data-stu-id="96294-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="96294-111">L’exécution est suspendu afin qu’un `AppDomain` peut être arrêté.</span><span class="sxs-lookup"><span data-stu-id="96294-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="96294-112">Quand l’exécution est suspendu, le runtime détermine quels threads se trouvent dans le `AppDomain` qui est en cours d’arrêter et de les définir à abandonner lorsqu’ils reprennent.</span><span class="sxs-lookup"><span data-stu-id="96294-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="96294-113">Il n’y aucun `AppDomain`-rappels spécifiques pendant cette interruption.</span><span class="sxs-lookup"><span data-stu-id="96294-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="96294-114">Le runtime est suspendu pour que la suspension de code peut se produire.</span><span class="sxs-lookup"><span data-stu-id="96294-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="96294-115">Suspension de code s’ensuit uniquement lorsque le compilateur (JIT) juste-à-temps est actif avec la suspension de code activée.</span><span class="sxs-lookup"><span data-stu-id="96294-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="96294-116">Code de rappels de suspension se produisent entre la `ICorProfilerCallback::RuntimeSuspendFinished` et `ICorProfilerCallback::RuntimeResumeStarted` rappels.</span><span class="sxs-lookup"><span data-stu-id="96294-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="96294-117">**Remarque :** le JIT CLR ne suspend pas les fonctions dans le .NET Framework version 2.0, cette valeur n’est pas utilisé dans la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="96294-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="96294-118">Le runtime est suspendu pour s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="96294-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="96294-119">Il doit suspendre tous les threads pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="96294-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="96294-120">Le runtime est suspendu dans le processus de débogage.</span><span class="sxs-lookup"><span data-stu-id="96294-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="96294-121">Le runtime est suspendu pour préparer un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="96294-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="96294-122">Le runtime est suspendu pour la recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="96294-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96294-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="96294-123">Remarks</span></span>  
 <span data-ttu-id="96294-124">Tous les threads d’exécution qui se trouvent dans le code non managé sont autorisés à continuer à s’exécuter jusqu'à ce qu’ils essaient d’entrer à nouveau l’exécution, à partir de laquelle ils seront également suspendus jusqu'à ce que le runtime reprend.</span><span class="sxs-lookup"><span data-stu-id="96294-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="96294-125">Cela s’applique également aux nouveaux threads qui entrent dans le runtime.</span><span class="sxs-lookup"><span data-stu-id="96294-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="96294-126">Tous les threads dans le runtime sont immédiatement suspendus s’ils sont dans du code interruptible, ou suspendus lorsqu’ils atteignent du code interruptible.</span><span class="sxs-lookup"><span data-stu-id="96294-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96294-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="96294-127">Requirements</span></span>  
 <span data-ttu-id="96294-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96294-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96294-129">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96294-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96294-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96294-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96294-131">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96294-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96294-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96294-132">See Also</span></span>  
 [<span data-ttu-id="96294-133">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="96294-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
