---
title: "ICorDebugDataTarget2::CreateVirtualUnwinder, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 421cff28e84106c0859889e6f9e99e870b469a98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="c8f48-102">ICorDebugDataTarget2::CreateVirtualUnwinder, méthode</span><span class="sxs-lookup"><span data-stu-id="c8f48-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="c8f48-103">Crée un dérouleur de pile qui commence le déroulement à partir d'un contexte initial (qui n'est pas forcément la feuille d'un thread).</span><span class="sxs-lookup"><span data-stu-id="c8f48-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8f48-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8f48-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c8f48-105">Parameters</span></span>  
 <span data-ttu-id="c8f48-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="c8f48-106">nativeThreadID</span></span>  
 <span data-ttu-id="c8f48-107">[in] L'ID de thread natif du thread à partir duquel dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="c8f48-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="c8f48-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="c8f48-108">contextFlags</span></span>  
 <span data-ttu-id="c8f48-109">[in] Indicateurs qui spécifient les parties du contexte définies dans `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="c8f48-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="c8f48-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="c8f48-110">cbContext</span></span>  
 <span data-ttu-id="c8f48-111">[in] Taille de `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="c8f48-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="c8f48-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="c8f48-112">initialContext</span></span>  
 <span data-ttu-id="c8f48-113">[in] Données dans le contexte.</span><span class="sxs-lookup"><span data-stu-id="c8f48-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="c8f48-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="c8f48-114">ppUnwinder</span></span>  
 <span data-ttu-id="c8f48-115">[out] Pointeur vers l'adresse d'un objet d'interface ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="c8f48-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8f48-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c8f48-116">Return Value</span></span>  
 <span data-ttu-id="c8f48-117">`S_OK` si l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="c8f48-117">`S_OK` if successful.</span></span> <span data-ttu-id="c8f48-118">Toute autre valeur `HRESULT` indique l'échec de l'opération.</span><span class="sxs-lookup"><span data-stu-id="c8f48-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="c8f48-119">Toute erreur `HRESULT` reçue par mscordbi est considérée comme irrécupérable [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) méthodes pour retourner `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="c8f48-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8f48-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="c8f48-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8f48-121">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c8f48-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f48-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c8f48-122">Requirements</span></span>  
 <span data-ttu-id="c8f48-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8f48-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f48-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8f48-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8f48-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8f48-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8f48-126">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8f48-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f48-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8f48-127">See Also</span></span>  
 [<span data-ttu-id="c8f48-128">Icordebugdatatarget2, Interface</span><span class="sxs-lookup"><span data-stu-id="c8f48-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="c8f48-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c8f48-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
