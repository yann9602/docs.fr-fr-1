---
title: "ICorDebugVirtualUnwinder::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4dc0b8bf7915fe579c4764bc06c1f2534eeb759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="f8055-102">ICorDebugVirtualUnwinder::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f8055-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="f8055-103">Avance jusqu'au contexte de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="f8055-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8055-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8055-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8055-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8055-105">Parameters</span></span>  
 <span data-ttu-id="f8055-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f8055-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8055-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8055-107">Return Value</span></span>  
 <span data-ttu-id="f8055-108">`S_OK` en cas de réussite du déroulement ou `CORDBG_S_AT_END_OF_STACK` si le déroulement ne peut pas être effectué étant donné qu'il ne reste plus de frames.</span><span class="sxs-lookup"><span data-stu-id="f8055-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="f8055-109">Si un HRESULT indiquant un échec est retourné, les API ICorDebug retournent `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="f8055-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8055-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="f8055-110">Remarks</span></span>  
 <span data-ttu-id="f8055-111">L'explorateur de pile doit vérifier sa progression vers l'avant. Ainsi, un appel à `Next` doit retourner un HRESULT indiquant un échec ou `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="f8055-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="f8055-112">Retour de `S_OK` indéfiniment peut provoquer une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="f8055-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8055-113">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f8055-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8055-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f8055-114">Requirements</span></span>  
 <span data-ttu-id="f8055-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8055-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8055-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8055-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8055-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8055-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8055-118">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8055-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8055-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8055-119">See Also</span></span>  
 [<span data-ttu-id="f8055-120">Icordebugmemorybuffer, Interface</span><span class="sxs-lookup"><span data-stu-id="f8055-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="f8055-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f8055-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
