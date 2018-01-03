---
title: "ICorDebugInternalFrame2::IsCloserToLeaf, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b6b769c25e0cd706eb57965b73d0fcfdcf9b9ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="28ab0-102">ICorDebugInternalFrame2::IsCloserToLeaf, méthode</span><span class="sxs-lookup"><span data-stu-id="28ab0-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="28ab0-103">Vérifie si le `this` frame interne est proche de la feuille de l’objet ICorDebugFrame spécifié.</span><span class="sxs-lookup"><span data-stu-id="28ab0-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ab0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28ab0-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28ab0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="28ab0-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="28ab0-106">[in] Un pointeur vers la comparaison `ICorDebugFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="28ab0-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="28ab0-107">[out] `true` si le `this` frame interne est proche de la feuille que le frame spécifié par `pFrameToCompare`; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="28ab0-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28ab0-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="28ab0-108">Return Value</span></span>  
 <span data-ttu-id="28ab0-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="28ab0-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="28ab0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28ab0-110">HRESULT</span></span>|<span data-ttu-id="28ab0-111">Description</span><span class="sxs-lookup"><span data-stu-id="28ab0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28ab0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="28ab0-112">S_OK</span></span>|<span data-ttu-id="28ab0-113">La comparaison a été effectuée avec succès.</span><span class="sxs-lookup"><span data-stu-id="28ab0-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="28ab0-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28ab0-114">E_FAIL</span></span>|<span data-ttu-id="28ab0-115">La comparaison n’a pas pu être effectuée.</span><span class="sxs-lookup"><span data-stu-id="28ab0-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="28ab0-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="28ab0-116">E_INVALIDARG</span></span>|<span data-ttu-id="28ab0-117">`pFrameToCompare` ou `pIsCloser` est null.</span><span class="sxs-lookup"><span data-stu-id="28ab0-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28ab0-118">Notes</span><span class="sxs-lookup"><span data-stu-id="28ab0-118">Remarks</span></span>  
 <span data-ttu-id="28ab0-119">`IsCloserToLeaf`peut être utilisé pour implémenter une stratégie pour entrelacer les frames internes avec d’autres frames sur la pile.</span><span class="sxs-lookup"><span data-stu-id="28ab0-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28ab0-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="28ab0-120">Requirements</span></span>  
 <span data-ttu-id="28ab0-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28ab0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28ab0-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28ab0-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28ab0-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28ab0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28ab0-124">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ab0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ab0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28ab0-125">See Also</span></span>  
 [<span data-ttu-id="28ab0-126">ICorDebugInternalFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="28ab0-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="28ab0-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="28ab0-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="28ab0-128">Débogage</span><span class="sxs-lookup"><span data-stu-id="28ab0-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
