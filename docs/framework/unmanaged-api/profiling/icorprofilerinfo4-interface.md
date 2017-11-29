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
ms.openlocfilehash: db91347ad2c951c28ea7b653336450929d37bdcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="22dec-102">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="22dec-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="22dec-103">Fournit des méthodes que les profileurs de code utilisent pour communiquer avec le common language runtime (CLR) pour contrôler la surveillance des événements et les informations de demande.</span><span class="sxs-lookup"><span data-stu-id="22dec-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="22dec-104">.</span><span class="sxs-lookup"><span data-stu-id="22dec-104">.</span></span> <span data-ttu-id="22dec-105">Le `ICorProfilerInfo4` interface est une extension de l’autre `ICorProfilerInfo` interfaces.</span><span class="sxs-lookup"><span data-stu-id="22dec-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="22dec-106">Il fournit de nouvelles méthodes pour prendre en charge de la recompilation juste-à-temps (JIT), ajoutée dans le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22dec-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22dec-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="22dec-107">Methods</span></span>  
  
|<span data-ttu-id="22dec-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="22dec-108">Method</span></span>|<span data-ttu-id="22dec-109">Description</span><span class="sxs-lookup"><span data-stu-id="22dec-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="22dec-110">EnumJITedFunctions2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="22dec-111">Retourne un énumérateur pour toutes les fonctions qui étaient précédemment compilé par JIT et recompilée juste.</span><span class="sxs-lookup"><span data-stu-id="22dec-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="22dec-112">EnumThreads (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="22dec-113">Obtient un énumérateur qui fournit des méthodes pour boucler séquentiellement dans la collection de tous les threads managés dans le processus profilé.</span><span class="sxs-lookup"><span data-stu-id="22dec-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="22dec-114">GetCodeInfo3 (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="22dec-115">Obtient les étendues de code natif associées à la version recompilée juste-à-temps de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="22dec-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="22dec-116">GetFunctionFromIP2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="22dec-117">Mappe un pointeur d’instruction de code managé vers la version recompilée juste-d’une fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="22dec-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="22dec-118">GetILToNativeMapping2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="22dec-119">Obtient un mappage à partir de Microsoft intermediate language (MSIL) aux offsets natifs pour le code contenu dans la version recompilée juste-de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="22dec-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="22dec-120">GetObjectSize2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="22dec-121">Retourne la taille d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="22dec-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="22dec-122">GetReJITIDs (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="22dec-123">Retourne un tableau d’ID qui identifie toutes les recompilée juste-versions de la fonction spécifiée qui sont toujours allouées.</span><span class="sxs-lookup"><span data-stu-id="22dec-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="22dec-124">InitializeCurrentThread (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="22dec-125">Initialise le thread actuel avant profiler ultérieur qu'appels d’API sur le même thread, afin que le blocage peut être évité.</span><span class="sxs-lookup"><span data-stu-id="22dec-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="22dec-126">RequestReJIT (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="22dec-127">Demande une recompilation juste-à-temps de toutes les instances des fonctions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="22dec-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="22dec-128">RequestRevert (méthode)</span><span class="sxs-lookup"><span data-stu-id="22dec-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="22dec-129">Rétablit les versions d'origine de toutes les instances des fonctions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="22dec-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22dec-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="22dec-130">Remarks</span></span>  
 <span data-ttu-id="22dec-131">Le CLR implémente les méthodes de l'interface `ICorProfilerInfo4` à l'aide du modèle libre de threads.</span><span class="sxs-lookup"><span data-stu-id="22dec-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="22dec-132">Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec.</span><span class="sxs-lookup"><span data-stu-id="22dec-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="22dec-133">Pour obtenir la liste des codes de retour possibles, consultez le fichier CorError.h.</span><span class="sxs-lookup"><span data-stu-id="22dec-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22dec-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="22dec-134">Requirements</span></span>  
 <span data-ttu-id="22dec-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22dec-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22dec-136">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22dec-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22dec-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22dec-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22dec-138">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22dec-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22dec-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22dec-139">See Also</span></span>  
 [<span data-ttu-id="22dec-140">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="22dec-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="22dec-141">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="22dec-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
