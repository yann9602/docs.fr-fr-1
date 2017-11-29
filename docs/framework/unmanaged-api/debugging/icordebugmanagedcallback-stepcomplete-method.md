---
title: "ICorDebugManagedCallback::StepComplete, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.StepComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eabc9a2730a1afdf574cee97a6f1b40bae34c7ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="20dbb-102">ICorDebugManagedCallback::StepComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="20dbb-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="20dbb-103">Notifie le débogueur qu’une étape est terminée.</span><span class="sxs-lookup"><span data-stu-id="20dbb-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20dbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20dbb-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20dbb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20dbb-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="20dbb-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread dans lequel l’étape est terminée.</span><span class="sxs-lookup"><span data-stu-id="20dbb-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="20dbb-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread dans lequel l’étape est terminée.</span><span class="sxs-lookup"><span data-stu-id="20dbb-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="20dbb-108">[in] Pointeur vers un objet ICorDebugStepper qui représente l’étape d’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="20dbb-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="20dbb-109">[in] Valeur de l’énumération CorDebugStepReason qui indique le résultat d’une étape individuelle.</span><span class="sxs-lookup"><span data-stu-id="20dbb-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20dbb-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="20dbb-110">Remarks</span></span>  
 <span data-ttu-id="20dbb-111">L’exécution pas à pas peut servir à se poursuivre pas à pas détaillé si vous le souhaitez, à moins que le débogage est arrêté.</span><span class="sxs-lookup"><span data-stu-id="20dbb-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20dbb-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="20dbb-112">Requirements</span></span>  
 <span data-ttu-id="20dbb-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20dbb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20dbb-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20dbb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20dbb-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20dbb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20dbb-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20dbb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20dbb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20dbb-117">See Also</span></span>  
 [<span data-ttu-id="20dbb-118">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="20dbb-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
