---
title: "ICorDebugController::Continue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Continue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 93fc138b8610d252be5c3ca3821bb1d41c5ac6ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="ee1b8-102">ICorDebugController::Continue, méthode</span><span class="sxs-lookup"><span data-stu-id="ee1b8-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="ee1b8-103">Reprend l’exécution de threads managés après un appel à [méthode Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="ee1b8-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee1b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee1b8-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee1b8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee1b8-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="ee1b8-106">[in] La valeur `true` s’il continue à partir d’un événement hors-bande ; sinon, valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="ee1b8-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee1b8-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ee1b8-107">Remarks</span></span>  
 <span data-ttu-id="ee1b8-108">`Continue`continue le processus après un appel à la `ICorDebugController::Stop` (méthode).</span><span class="sxs-lookup"><span data-stu-id="ee1b8-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="ee1b8-109">Lorsque vous effectuez un débogage en mode mixte, n’appelez pas `Continue` sur Win32 thread d’événement, sauf si vous continuez à partir d’un événement hors-bande.</span><span class="sxs-lookup"><span data-stu-id="ee1b8-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="ee1b8-110">Un *événement dans la bande* est un événement managé ou un événement non managé normal pendant lequel le débogueur prend en charge l’interaction avec l’état managé du processus.</span><span class="sxs-lookup"><span data-stu-id="ee1b8-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="ee1b8-111">Dans ce cas, le débogueur reçoit le [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) rappel avec son `fOutOfBand` paramètre la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="ee1b8-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="ee1b8-112">Un *out-of-band événement* est un événement non managé pendant lequel l’interaction avec l’état managé du processus est impossible pendant que le processus est arrêté en raison de l’événement.</span><span class="sxs-lookup"><span data-stu-id="ee1b8-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="ee1b8-113">Dans ce cas, le débogueur reçoit le `ICorDebugUnmanagedCallback::DebugEvent` rappel avec son `fOutOfBand` paramètre la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ee1b8-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee1b8-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ee1b8-114">Requirements</span></span>  
 <span data-ttu-id="ee1b8-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee1b8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee1b8-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee1b8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee1b8-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee1b8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee1b8-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee1b8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1b8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee1b8-119">See Also</span></span>  
 
