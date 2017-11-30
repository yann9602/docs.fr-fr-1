---
title: COR_PRF_GC_GENERATION_RANGE, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION_RANGE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords: COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e2fd546a88f34906ab37e36377f67c26e80b2799
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcgenerationrange-structure"></a><span data-ttu-id="1b910-102">COR_PRF_GC_GENERATION_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="1b910-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="1b910-103">Décrit une plage (un bloc) de mémoire qui va faire l’objet d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1b910-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b910-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b910-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="1b910-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1b910-105">Members</span></span>  
  
|<span data-ttu-id="1b910-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1b910-106">Member</span></span>|<span data-ttu-id="1b910-107">Description</span><span class="sxs-lookup"><span data-stu-id="1b910-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="1b910-108">Une valeur de la [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) appartient d’énumération qui spécifie la génération à laquelle le bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="1b910-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="1b910-109">L’ID d’un objet qui spécifie l’emplacement de départ du bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="1b910-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="1b910-110">Pointeur vers un entier qui spécifie la taille de la partie utilisée du bloc de mémoire (autrement dit, la quantité de mémoire utilisée dans le bloc).</span><span class="sxs-lookup"><span data-stu-id="1b910-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="1b910-111">Pointeur vers un entier qui spécifie la taille du bloc de mémoire (autrement dit, la quantité de mémoire réservée pour le bloc).</span><span class="sxs-lookup"><span data-stu-id="1b910-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b910-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="1b910-112">Remarks</span></span>  
 <span data-ttu-id="1b910-113">Le `rangeLength` valeur est garantie exacte uniquement si [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) ou [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), tous deux utilisent le `COR_PRF_GC_GENERATION_RANGE` la structure, est appelée à partir de la [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ou [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="1b910-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b910-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1b910-114">Requirements</span></span>  
 <span data-ttu-id="1b910-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b910-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b910-116">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1b910-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1b910-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b910-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b910-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b910-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b910-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b910-119">See Also</span></span>  
 [<span data-ttu-id="1b910-120">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="1b910-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
