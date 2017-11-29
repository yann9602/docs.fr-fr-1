---
title: "ICorDebugInternalFrame2::GetFrameAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.GetFrameAddress Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ee867afe99fc5d2f2eb27bb1e6888aef8341d71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="354d3-102">ICorDebugInternalFrame2::GetFrameAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="354d3-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="354d3-103">Retourne l’adresse de la pile du frame interne.</span><span class="sxs-lookup"><span data-stu-id="354d3-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="354d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="354d3-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="354d3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="354d3-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="354d3-106">[out] Pointeur vers le `CORDB_ADDRESS` pour le frame interne.</span><span class="sxs-lookup"><span data-stu-id="354d3-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="354d3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="354d3-107">Return Value</span></span>  
 <span data-ttu-id="354d3-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="354d3-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="354d3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="354d3-109">HRESULT</span></span>|<span data-ttu-id="354d3-110">Description</span><span class="sxs-lookup"><span data-stu-id="354d3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="354d3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="354d3-111">S_OK</span></span>|<span data-ttu-id="354d3-112">L’adresse du frame interne a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="354d3-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="354d3-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="354d3-113">E_FAIL</span></span>|<span data-ttu-id="354d3-114">L’adresse du frame interne n’a pas pu être retourné.</span><span class="sxs-lookup"><span data-stu-id="354d3-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="354d3-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="354d3-115">E_INVALIDARG</span></span>|<span data-ttu-id="354d3-116">`pAddress` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="354d3-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="354d3-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="354d3-117">Remarks</span></span>  
 <span data-ttu-id="354d3-118">La valeur retournée dans `pAddress` peut être utilisé pour déterminer l’emplacement du frame interne par rapport aux autres frames sur la pile.</span><span class="sxs-lookup"><span data-stu-id="354d3-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="354d3-119">Même sur les ordinateurs basés sur IA-64, le frame interne vit uniquement sur la pile, et il n’existe aucun pointeur correspondant vers un magasin de stockage.</span><span class="sxs-lookup"><span data-stu-id="354d3-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="354d3-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="354d3-120">Requirements</span></span>  
 <span data-ttu-id="354d3-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="354d3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="354d3-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="354d3-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="354d3-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="354d3-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="354d3-124">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="354d3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354d3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="354d3-125">See Also</span></span>  
 [<span data-ttu-id="354d3-126">ICorDebugInternalFrame2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="354d3-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="354d3-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="354d3-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="354d3-128">Débogage</span><span class="sxs-lookup"><span data-stu-id="354d3-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
