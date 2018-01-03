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
ms.workload: dotnet
ms.openlocfilehash: 267bc2fcd03786bfceb218dd0218ffa7006f8fa7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="c736a-102">ICorDebugNativeFrame2::IsChild, méthode</span><span class="sxs-lookup"><span data-stu-id="c736a-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="c736a-103">Détermine si le frame actuel est un frame enfant.</span><span class="sxs-lookup"><span data-stu-id="c736a-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c736a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c736a-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c736a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c736a-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="c736a-106">[out] Valeur booléenne qui spécifie si le frame actuel est un frame enfant.</span><span class="sxs-lookup"><span data-stu-id="c736a-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c736a-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c736a-107">Return Value</span></span>  
 <span data-ttu-id="c736a-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c736a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c736a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c736a-109">HRESULT</span></span>|<span data-ttu-id="c736a-110">Description</span><span class="sxs-lookup"><span data-stu-id="c736a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c736a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c736a-111">S_OK</span></span>|<span data-ttu-id="c736a-112">L’état enfant a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c736a-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="c736a-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c736a-113">E_FAIL</span></span>|<span data-ttu-id="c736a-114">L’état de l’enfant n’a pas pu être retourné.</span><span class="sxs-lookup"><span data-stu-id="c736a-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="c736a-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c736a-115">E_INVALIDARG</span></span>|<span data-ttu-id="c736a-116">`pIsChild` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="c736a-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="c736a-117">Exceptions</span><span class="sxs-lookup"><span data-stu-id="c736a-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c736a-118">Notes</span><span class="sxs-lookup"><span data-stu-id="c736a-118">Remarks</span></span>  
 <span data-ttu-id="c736a-119">Le `IsChild` retourne de la méthode `true` si l’objet frame sur lequel vous appelez la méthode est un enfant d’un autre frame.</span><span class="sxs-lookup"><span data-stu-id="c736a-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="c736a-120">Si c’est le cas, utilisez le [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) méthode permettant de vérifier si un frame est son parent.</span><span class="sxs-lookup"><span data-stu-id="c736a-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c736a-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c736a-121">Requirements</span></span>  
 <span data-ttu-id="c736a-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c736a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c736a-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c736a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c736a-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c736a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c736a-125">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c736a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c736a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c736a-126">See Also</span></span>  
 [<span data-ttu-id="c736a-127">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="c736a-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="c736a-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c736a-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c736a-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="c736a-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
