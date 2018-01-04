---
title: "COR_PRF_TRANSITION_REASON, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_TRANSITION_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_TRANSITION_REASON
helpviewer_keywords: COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 498abc57e35946b2b0c8bf08cdd768bd7039c9f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="b5477-102">COR_PRF_TRANSITION_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="b5477-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="b5477-103">Indique la raison d'une transition de code managé en code non managé, ou l'inverse.</span><span class="sxs-lookup"><span data-stu-id="b5477-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5477-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5477-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="b5477-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b5477-105">Members</span></span>  
  
|<span data-ttu-id="b5477-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b5477-106">Member</span></span>|<span data-ttu-id="b5477-107">Description</span><span class="sxs-lookup"><span data-stu-id="b5477-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="b5477-108">La transition est en raison d’un appel dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="b5477-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="b5477-109">La transition est dû à un retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="b5477-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5477-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b5477-110">Remarks</span></span>  
 <span data-ttu-id="b5477-111">Lorsqu’une transition se produit, le profileur reçoit un [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) ou [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) rappel, qui Fournit une valeur de la `COR_PRF_TRANSITION_REASON` énumération pour indiquer la raison de la transition.</span><span class="sxs-lookup"><span data-stu-id="b5477-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5477-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b5477-112">Requirements</span></span>  
 <span data-ttu-id="b5477-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5477-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5477-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5477-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5477-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5477-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5477-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5477-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
