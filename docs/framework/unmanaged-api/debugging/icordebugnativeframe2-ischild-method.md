---
title: "ICorDebugNativeFrame2::IsChild, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsChild Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 006543e473ca3b7cc1818b2b4641567ce37f6f0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="4fb6c-102">ICorDebugNativeFrame2::IsChild, méthode</span><span class="sxs-lookup"><span data-stu-id="4fb6c-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="4fb6c-103">Détermine si le frame actuel est un frame enfant.</span><span class="sxs-lookup"><span data-stu-id="4fb6c-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fb6c-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fb6c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4fb6c-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="4fb6c-106">[out] Valeur booléenne qui spécifie si le frame actuel est un frame enfant.</span><span class="sxs-lookup"><span data-stu-id="4fb6c-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fb6c-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4fb6c-107">Return Value</span></span>  
 <span data-ttu-id="4fb6c-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4fb6c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4fb6c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4fb6c-109">HRESULT</span></span>|<span data-ttu-id="4fb6c-110">Description</span><span class="sxs-lookup"><span data-stu-id="4fb6c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4fb6c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4fb6c-111">S_OK</span></span>|<span data-ttu-id="4fb6c-112">L’état enfant a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="4fb6c-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="4fb6c-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4fb6c-113">E_FAIL</span></span>|<span data-ttu-id="4fb6c-114">L’état de l’enfant n’a pas pu être retourné.</span><span class="sxs-lookup"><span data-stu-id="4fb6c-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="4fb6c-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4fb6c-115">E_INVALIDARG</span></span>|<span data-ttu-id="4fb6c-116">`pIsChild` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="4fb6c-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="4fb6c-117">Exceptions</span><span class="sxs-lookup"><span data-stu-id="4fb6c-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fb6c-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="4fb6c-118">Remarks</span></span>  
 <span data-ttu-id="4fb6c-119">Le `IsChild` retourne de la méthode `true` si l’objet frame sur lequel vous appelez la méthode est un enfant d’un autre frame.</span><span class="sxs-lookup"><span data-stu-id="4fb6c-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="4fb6c-120">Si c’est le cas, utilisez le [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) méthode permettant de vérifier si un frame est son parent.</span><span class="sxs-lookup"><span data-stu-id="4fb6c-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fb6c-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4fb6c-121">Requirements</span></span>  
 <span data-ttu-id="4fb6c-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fb6c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fb6c-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fb6c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fb6c-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fb6c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fb6c-125">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fb6c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb6c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fb6c-126">See Also</span></span>  
 [<span data-ttu-id="4fb6c-127">ICorDebugNativeFrame2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="4fb6c-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="4fb6c-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4fb6c-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4fb6c-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="4fb6c-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
