---
title: COR_PRF_EX_CLAUSE_INFO, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_EX_CLAUSE_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords: COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65025384aa94ac363336bae7f37f8ea88a3bab67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="cecf7-102">COR_PRF_EX_CLAUSE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="cecf7-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="cecf7-103">Stocke des informations sur une instance de clause d'exception spécifique et sa trame associée.</span><span class="sxs-lookup"><span data-stu-id="cecf7-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cecf7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cecf7-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="cecf7-105">Membres</span><span class="sxs-lookup"><span data-stu-id="cecf7-105">Members</span></span>  
  
|<span data-ttu-id="cecf7-106">Membre</span><span class="sxs-lookup"><span data-stu-id="cecf7-106">Member</span></span>|<span data-ttu-id="cecf7-107">Description</span><span class="sxs-lookup"><span data-stu-id="cecf7-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="cecf7-108">Une valeur de la [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) énumération qui spécifie le type de clause d’exception le code entré ou à gauche.</span><span class="sxs-lookup"><span data-stu-id="cecf7-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="cecf7-109">Le point d’entrée natif du Gestionnaire de clause — par exemple, le contenu du Registre X86 EIP.</span><span class="sxs-lookup"><span data-stu-id="cecf7-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="cecf7-110">Le pointeur vers le frame logique pour le Gestionnaire de clause — par exemple, le contenu du Registre X86 EBP.</span><span class="sxs-lookup"><span data-stu-id="cecf7-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="cecf7-111">Pointeur vers la pile cachée.</span><span class="sxs-lookup"><span data-stu-id="cecf7-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="cecf7-112">Cette valeur est le contenu du Registre BSP et s’applique uniquement à IA64.</span><span class="sxs-lookup"><span data-stu-id="cecf7-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cecf7-113">Notes</span><span class="sxs-lookup"><span data-stu-id="cecf7-113">Remarks</span></span>  
 <span data-ttu-id="cecf7-114">Lorsqu’une notification d’exception est reçue, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) peut être utilisé pour obtenir les informations d’adresse et d’image natives pour la clause d’exception (`catch` / `finally`/filtre) qui doit être exécutée ou vient d’être exécutée.</span><span class="sxs-lookup"><span data-stu-id="cecf7-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="cecf7-115">L’exécution d’une clause d’exception implique ces rappels dans le common language runtime (CLR) :</span><span class="sxs-lookup"><span data-stu-id="cecf7-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="cecf7-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="cecf7-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="cecf7-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="cecf7-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="cecf7-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="cecf7-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="cecf7-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="cecf7-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="cecf7-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="cecf7-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="cecf7-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="cecf7-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="cecf7-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cecf7-122">Requirements</span></span>  
 <span data-ttu-id="cecf7-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cecf7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cecf7-124">**En-tête :** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="cecf7-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="cecf7-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cecf7-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cecf7-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cecf7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecf7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cecf7-127">See Also</span></span>  
 [<span data-ttu-id="cecf7-128">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="cecf7-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
