---
title: "ICorDebugStepper::Step, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Step
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 914773adefd2ed4c1aa98310fd27a0cbc829bf49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="5fb5c-102">ICorDebugStepper::Step, méthode</span><span class="sxs-lookup"><span data-stu-id="5fb5c-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="5fb5c-103">Entraîne ce ICorDebugStepper à pas son thread conteneur et éventuellement, continuez le pas à pas via des fonctions appelées dans le thread.</span><span class="sxs-lookup"><span data-stu-id="5fb5c-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fb5c-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fb5c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5fb5c-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="5fb5c-106">[in] La valeur `true` à l’étape dans une fonction qui est appelée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="5fb5c-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="5fb5c-107">La valeur `false` à l’étape de la fonction.</span><span class="sxs-lookup"><span data-stu-id="5fb5c-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fb5c-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="5fb5c-108">Remarks</span></span>  
 <span data-ttu-id="5fb5c-109">L’étape se termine lorsque le common language runtime exécute l’instruction managée suivante dans le cadre de cette exécution pas à pas.</span><span class="sxs-lookup"><span data-stu-id="5fb5c-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="5fb5c-110">Si `Step` est appelée sur une exécution pas à pas, ce qui n’est pas dans le code managé, l’étape se termine lorsque l’instruction de code managé suivante est exécutée par le thread.</span><span class="sxs-lookup"><span data-stu-id="5fb5c-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fb5c-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5fb5c-111">Requirements</span></span>  
 <span data-ttu-id="5fb5c-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fb5c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fb5c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fb5c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fb5c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fb5c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fb5c-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fb5c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
