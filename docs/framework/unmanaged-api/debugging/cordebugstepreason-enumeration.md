---
title: "CorDebugStepReason, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStepReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugStepReason
helpviewer_keywords: CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 68c4f9452f8ccc9b4d48ee67755a311f32540247
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="1ff30-102">CorDebugStepReason, énumération</span><span class="sxs-lookup"><span data-stu-id="1ff30-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="1ff30-103">Indique le résultat d'une étape individuelle.</span><span class="sxs-lookup"><span data-stu-id="1ff30-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ff30-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="1ff30-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1ff30-105">Members</span></span>  
  
|<span data-ttu-id="1ff30-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1ff30-106">Member</span></span>|<span data-ttu-id="1ff30-107">Description</span><span class="sxs-lookup"><span data-stu-id="1ff30-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="1ff30-108">Exécution pas à pas s’est terminée normalement, dans la même fonction.</span><span class="sxs-lookup"><span data-stu-id="1ff30-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="1ff30-109">Exécution pas à pas a continué normalement, une fois que la fonction a renvoyé.</span><span class="sxs-lookup"><span data-stu-id="1ff30-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="1ff30-110">Exécution pas à pas a continué normalement, au début d’une fonction qui vient d’être appelée.</span><span class="sxs-lookup"><span data-stu-id="1ff30-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="1ff30-111">Une exception a été générée et le contrôle a été passé à un filtre d’exception.</span><span class="sxs-lookup"><span data-stu-id="1ff30-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="1ff30-112">Une exception a été générée et le contrôle a été passé à un gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="1ff30-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="1ff30-113">Contrôle a été passé à un intercepteur.</span><span class="sxs-lookup"><span data-stu-id="1ff30-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="1ff30-114">Le thread est arrêté avant la fin de l’étape.</span><span class="sxs-lookup"><span data-stu-id="1ff30-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ff30-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1ff30-115">Requirements</span></span>  
 <span data-ttu-id="1ff30-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ff30-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ff30-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ff30-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ff30-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ff30-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ff30-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff30-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff30-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ff30-120">See Also</span></span>  
 [<span data-ttu-id="1ff30-121">StepComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="1ff30-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [<span data-ttu-id="1ff30-122">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="1ff30-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
