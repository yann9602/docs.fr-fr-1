---
title: "ICorDebugNativeFrame2::GetStackParameterSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.GetStackParameterSize Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa7e67c252f2ece16c072e22d0333e085fbc4f65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="b7224-102">ICorDebugNativeFrame2::GetStackParameterSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b7224-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="b7224-103">Retourne la taille cumulée des paramètres de la pile sur x86 systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b7224-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7224-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7224-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7224-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7224-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="b7224-106">[out] Pointeur vers la taille cumulée des paramètres sur la pile.</span><span class="sxs-lookup"><span data-stu-id="b7224-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7224-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b7224-107">Return Value</span></span>  
 <span data-ttu-id="b7224-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b7224-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b7224-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7224-109">HRESULT</span></span>|<span data-ttu-id="b7224-110">Description</span><span class="sxs-lookup"><span data-stu-id="b7224-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7224-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7224-111">S_OK</span></span>|<span data-ttu-id="b7224-112">La taille de pile a été retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="b7224-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="b7224-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b7224-113">S_FALSE</span></span>|<span data-ttu-id="b7224-114">`GetStackParameterSize`a été appelé sur une plateforme non x86.</span><span class="sxs-lookup"><span data-stu-id="b7224-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="b7224-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7224-115">E_FAIL</span></span>|<span data-ttu-id="b7224-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="b7224-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="b7224-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b7224-117">E_INVALIDARG</span></span>|<span data-ttu-id="b7224-118">`pSize`Est `null`.</span><span class="sxs-lookup"><span data-stu-id="b7224-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b7224-119">Exceptions</span><span class="sxs-lookup"><span data-stu-id="b7224-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7224-120">Notes</span><span class="sxs-lookup"><span data-stu-id="b7224-120">Remarks</span></span>  
 <span data-ttu-id="b7224-121">Le [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) méthodes ne s’ajustent pas le pointeur de pile pour les paramètres qui sont envoyées sur la pile.</span><span class="sxs-lookup"><span data-stu-id="b7224-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="b7224-122">Au lieu de cela, vous pouvez utiliser la valeur retournée par `GetStackParameterSize` pour ajuster le pointeur de pile pour amorcer un dérouleur natif, qui effectue l’ajustement pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="b7224-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7224-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b7224-123">Requirements</span></span>  
 <span data-ttu-id="b7224-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7224-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7224-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7224-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7224-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7224-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7224-127">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7224-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7224-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7224-128">See Also</span></span>  
 [<span data-ttu-id="b7224-129">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="b7224-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="b7224-130">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b7224-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b7224-131">Débogage</span><span class="sxs-lookup"><span data-stu-id="b7224-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
