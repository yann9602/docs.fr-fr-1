---
title: "ICorDebugStackWalk::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.Next Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a776f215d67c381a1c08416927cabd3ccb40afa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="4605b-102">ICorDebugStackWalk::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="4605b-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="4605b-103">Déplace le [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objet à l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="4605b-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4605b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4605b-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4605b-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4605b-105">Return Value</span></span>  
 <span data-ttu-id="4605b-106">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4605b-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4605b-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4605b-107">HRESULT</span></span>|<span data-ttu-id="4605b-108">Description</span><span class="sxs-lookup"><span data-stu-id="4605b-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4605b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="4605b-109">S_OK</span></span>|<span data-ttu-id="4605b-110">Le runtime s’est correctement déroulé le frame suivant (voir Remarques).</span><span class="sxs-lookup"><span data-stu-id="4605b-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="4605b-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4605b-111">E_FAIL</span></span>|<span data-ttu-id="4605b-112">Le `ICorDebugStackWalk` objet n’a pas pu être avancé.</span><span class="sxs-lookup"><span data-stu-id="4605b-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="4605b-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="4605b-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="4605b-114">La fin de la pile a été atteinte suite à ce déroulement.</span><span class="sxs-lookup"><span data-stu-id="4605b-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="4605b-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="4605b-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="4605b-116">Le pointeur de frame est déjà à la fin de la pile. Par conséquent, aucun frame supplémentaire n’est accessible.</span><span class="sxs-lookup"><span data-stu-id="4605b-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="4605b-117">Exceptions</span><span class="sxs-lookup"><span data-stu-id="4605b-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4605b-118">Notes</span><span class="sxs-lookup"><span data-stu-id="4605b-118">Remarks</span></span>  
 <span data-ttu-id="4605b-119">Le `Next` méthode avance le `ICorDebugStackWalk` de l’objet au frame appelant seulement si le runtime peut dérouler le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="4605b-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="4605b-120">Dans le cas contraire, l’objet avance le frame suivant que le runtime est en mesure de dérouler.</span><span class="sxs-lookup"><span data-stu-id="4605b-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4605b-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4605b-121">Requirements</span></span>  
 <span data-ttu-id="4605b-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4605b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4605b-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4605b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4605b-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4605b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4605b-125">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4605b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4605b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4605b-126">See Also</span></span>  
 [<span data-ttu-id="4605b-127">ICorDebugStackWalk, interface</span><span class="sxs-lookup"><span data-stu-id="4605b-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="4605b-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4605b-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4605b-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="4605b-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
