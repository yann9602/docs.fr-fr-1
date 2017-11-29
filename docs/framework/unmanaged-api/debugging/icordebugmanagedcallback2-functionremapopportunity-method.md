---
title: "ICorDebugManagedCallback2::FunctionRemapOpportunity, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a8360913597dfb5156399a45f86d2cc1a9f453d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="79f08-102">ICorDebugManagedCallback2::FunctionRemapOpportunity, méthode</span><span class="sxs-lookup"><span data-stu-id="79f08-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="79f08-103">Notifie le débogueur que l’exécution du code a atteint un point de séquence dans une version antérieure d’une fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="79f08-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79f08-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79f08-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79f08-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="79f08-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="79f08-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="79f08-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel le point d’arrêt de remappage a été rencontrée.</span><span class="sxs-lookup"><span data-stu-id="79f08-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="79f08-108">[in] Pointeur vers un objet ICorDebugFunction qui représente la version de la fonction en cours d’exécution sur le thread.</span><span class="sxs-lookup"><span data-stu-id="79f08-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="79f08-109">[in] Pointeur vers un objet ICorDebugFunction qui représente la version la plus récente de la fonction.</span><span class="sxs-lookup"><span data-stu-id="79f08-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="79f08-110">[in] L’offset Microsoft intermediate language (MSIL), du pointeur d’instruction dans l’ancienne version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="79f08-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79f08-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="79f08-111">Remarks</span></span>  
 <span data-ttu-id="79f08-112">Ce rappel permet au débogueur de remapper le pointeur d’instruction à son emplacement approprié dans la nouvelle version de la fonction spécifiée en appelant le [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="79f08-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="79f08-113">Si le débogueur n’appelle pas `RemapFunction` avant d’appeler le [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) (méthode), le runtime continue à exécuter l’ancien code et déclenchera un autre `FunctionRemapOpportunity` rappel au point de séquence suivant.</span><span class="sxs-lookup"><span data-stu-id="79f08-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="79f08-114">Ce rappel est appelé pour chaque frame qui exécute une ancienne version de la fonction donnée jusqu'à ce que le débogueur retourne S_OK.</span><span class="sxs-lookup"><span data-stu-id="79f08-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79f08-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="79f08-115">Requirements</span></span>  
 <span data-ttu-id="79f08-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79f08-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79f08-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79f08-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79f08-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79f08-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79f08-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79f08-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f08-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79f08-120">See Also</span></span>  
 [<span data-ttu-id="79f08-121">ICorDebugManagedCallback2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="79f08-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="79f08-122">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="79f08-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
