---
title: "ICorDebugStepper::StepRange, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a02efe1b701506cc3de695c5b79d5e9c84b25b8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="1d122-102">ICorDebugStepper::StepRange, méthode</span><span class="sxs-lookup"><span data-stu-id="1d122-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="1d122-103">Provoque un ICorDebugStepper pas à pas son thread conteneur et à retourner lorsqu’il atteint le code situé au-delà de la dernière des plages spécifiées.</span><span class="sxs-lookup"><span data-stu-id="1d122-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d122-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d122-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d122-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d122-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="1d122-106">[in] La valeur `true` à l’étape dans une fonction qui est appelée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="1d122-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="1d122-107">La valeur `false` à l’étape de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1d122-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="1d122-108">[in] Tableau de structures COR_DEBUG_STEP_RANGE, chacun spécifiant une plage.</span><span class="sxs-lookup"><span data-stu-id="1d122-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="1d122-109">[in] Taille du tableau `ranges`.</span><span class="sxs-lookup"><span data-stu-id="1d122-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d122-110">Notes</span><span class="sxs-lookup"><span data-stu-id="1d122-110">Remarks</span></span>  
 <span data-ttu-id="1d122-111">Le `StepRange` méthode fonctionne comme la [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) (méthode), sauf qu’elle ne se termine pas tant que le code en dehors de la plage donnée est atteinte.</span><span class="sxs-lookup"><span data-stu-id="1d122-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="1d122-112">Cela peut être plus efficace que l’exécution pas à pas d’une instruction à la fois.</span><span class="sxs-lookup"><span data-stu-id="1d122-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="1d122-113">Les plages sont spécifiées sous forme de liste de paires d’offsets à partir du début du frame de d’exécution pas à pas.</span><span class="sxs-lookup"><span data-stu-id="1d122-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="1d122-114">Les plages sont relatives au code Microsoft intermediate language (MSIL) d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="1d122-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="1d122-115">Appelez [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) avec `false` pour que les plages par rapport au code natif d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="1d122-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d122-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1d122-116">Requirements</span></span>  
 <span data-ttu-id="1d122-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d122-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d122-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d122-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d122-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d122-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d122-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d122-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
