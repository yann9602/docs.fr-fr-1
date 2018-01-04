---
title: ICorProfilerInfo4, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83629d0fc8288d118ec31c38473cb63335bb1d48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="be60b-102">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="be60b-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="be60b-103">Fournit des méthodes que les profileurs de code utilisent pour communiquer avec le common language runtime (CLR) pour contrôler la surveillance des événements et les informations de demande.</span><span class="sxs-lookup"><span data-stu-id="be60b-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="be60b-104">.</span><span class="sxs-lookup"><span data-stu-id="be60b-104">.</span></span> <span data-ttu-id="be60b-105">Le `ICorProfilerInfo4` interface est une extension de l’autre `ICorProfilerInfo` interfaces.</span><span class="sxs-lookup"><span data-stu-id="be60b-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="be60b-106">Il fournit de nouvelles méthodes pour prendre en charge de la recompilation juste-à-temps (JIT), ajoutée dans le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be60b-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be60b-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="be60b-107">Methods</span></span>  
  
|<span data-ttu-id="be60b-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-108">Method</span></span>|<span data-ttu-id="be60b-109">Description</span><span class="sxs-lookup"><span data-stu-id="be60b-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be60b-110">EnumJITedFunctions2, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="be60b-111">Retourne un énumérateur pour toutes les fonctions qui étaient précédemment compilé par JIT et recompilée juste.</span><span class="sxs-lookup"><span data-stu-id="be60b-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="be60b-112">EnumThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="be60b-113">Obtient un énumérateur qui fournit des méthodes pour boucler séquentiellement dans la collection de tous les threads managés dans le processus profilé.</span><span class="sxs-lookup"><span data-stu-id="be60b-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="be60b-114">GetCodeInfo3, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="be60b-115">Obtient les étendues de code natif associées à la version recompilée juste-à-temps de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="be60b-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="be60b-116">GetFunctionFromIP2, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="be60b-117">Mappe un pointeur d’instruction de code managé vers la version recompilée juste-d’une fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="be60b-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="be60b-118">GetILToNativeMapping2, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="be60b-119">Obtient un mappage à partir de Microsoft intermediate language (MSIL) aux offsets natifs pour le code contenu dans la version recompilée juste-de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="be60b-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="be60b-120">GetObjectSize2, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="be60b-121">Retourne la taille d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="be60b-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="be60b-122">GetReJITIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="be60b-123">Retourne un tableau d’ID qui identifie toutes les recompilée juste-versions de la fonction spécifiée qui sont toujours allouées.</span><span class="sxs-lookup"><span data-stu-id="be60b-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="be60b-124">InitializeCurrentThread, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="be60b-125">Initialise le thread actuel avant profiler ultérieur qu'appels d’API sur le même thread, afin que le blocage peut être évité.</span><span class="sxs-lookup"><span data-stu-id="be60b-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="be60b-126">RequestReJIT, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="be60b-127">Demande une recompilation juste-à-temps de toutes les instances des fonctions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="be60b-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="be60b-128">RequestRevert, méthode</span><span class="sxs-lookup"><span data-stu-id="be60b-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="be60b-129">Rétablit les versions d'origine de toutes les instances des fonctions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="be60b-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be60b-130">Notes</span><span class="sxs-lookup"><span data-stu-id="be60b-130">Remarks</span></span>  
 <span data-ttu-id="be60b-131">Le CLR implémente les méthodes de l'interface `ICorProfilerInfo4` à l'aide du modèle libre de threads.</span><span class="sxs-lookup"><span data-stu-id="be60b-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="be60b-132">Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec.</span><span class="sxs-lookup"><span data-stu-id="be60b-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="be60b-133">Pour obtenir la liste des codes de retour possibles, consultez le fichier CorError.h.</span><span class="sxs-lookup"><span data-stu-id="be60b-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be60b-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="be60b-134">Requirements</span></span>  
 <span data-ttu-id="be60b-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be60b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be60b-136">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be60b-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be60b-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be60b-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be60b-138">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be60b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be60b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be60b-139">See Also</span></span>  
 [<span data-ttu-id="be60b-140">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="be60b-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="be60b-141">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="be60b-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
