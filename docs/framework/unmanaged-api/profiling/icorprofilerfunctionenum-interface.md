---
title: ICorProfilerFunctionEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum
helpviewer_keywords: ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1067fa6738b23492b3a58500b4cb6ba1d030304f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="064d0-102">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="064d0-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="064d0-103">Fournit des méthodes pour itérer séquentiellement une collection de fonctions dans le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="064d0-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="064d0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="064d0-104">Methods</span></span>  
  
|<span data-ttu-id="064d0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="064d0-105">Method</span></span>|<span data-ttu-id="064d0-106">Description</span><span class="sxs-lookup"><span data-stu-id="064d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="064d0-107">Clone (méthode)</span><span class="sxs-lookup"><span data-stu-id="064d0-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="064d0-108">Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerFunctionEnum`.</span><span class="sxs-lookup"><span data-stu-id="064d0-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="064d0-109">GetCount (méthode)</span><span class="sxs-lookup"><span data-stu-id="064d0-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="064d0-110">Obtient le nombre de fonctions qui ont été chargées par l'application ou chargées de force par le profileur.</span><span class="sxs-lookup"><span data-stu-id="064d0-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="064d0-111">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="064d0-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="064d0-112">Obtient le nombre spécifié de fonctions contiguës dans une collection séquentielle de fonctions, à commencer par la position actuelle de l’énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="064d0-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="064d0-113">Reset (méthode)</span><span class="sxs-lookup"><span data-stu-id="064d0-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="064d0-114">Déplace le curseur de l'énumérateur à la position de départ de la séquence.</span><span class="sxs-lookup"><span data-stu-id="064d0-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="064d0-115">Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="064d0-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="064d0-116">Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="064d0-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="064d0-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="064d0-117">Remarks</span></span>  
 <span data-ttu-id="064d0-118">L'interface `ICorProfilerFunctionEnum` est un énumérateur.</span><span class="sxs-lookup"><span data-stu-id="064d0-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="064d0-119">Elle permet au récepteur d'un tableau de récupérer des éléments de l'expéditeur à une fréquence appropriée pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="064d0-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="064d0-120">En d'autres termes, le récepteur peut contrôler explicitement le flux d'éléments de tableau et éviter ainsi les problèmes liés au passage de tableaux volumineux en tant que paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="064d0-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="064d0-121">`ICorProfilerFunctionEnum` énumère les fonctions qui ont déjà été compilées juste-à-temps, mais n'inclut pas les fonctions chargées à partir des images natives générées avec Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="064d0-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="064d0-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="064d0-122">Requirements</span></span>  
 <span data-ttu-id="064d0-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="064d0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="064d0-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="064d0-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="064d0-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="064d0-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="064d0-126">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="064d0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064d0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="064d0-127">See Also</span></span>  
 [<span data-ttu-id="064d0-128">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="064d0-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="064d0-129">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="064d0-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="064d0-130">EnumJITedFunctions (méthode)</span><span class="sxs-lookup"><span data-stu-id="064d0-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
