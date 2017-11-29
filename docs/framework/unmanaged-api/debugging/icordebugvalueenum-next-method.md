---
title: "ICorDebugValueEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 71775db7134c8f376099b0820f4330602d3db0e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="c0ab4-102">ICorDebugValueEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="c0ab4-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="c0ab4-103">Obtient le nombre spécifié d’instances de « ICorDebugValue » à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="c0ab4-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0ab4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0ab4-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0ab4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0ab4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c0ab4-106">[in] Le nombre de `ICorDebugValue` instances doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="c0ab4-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="c0ab4-107">[out] Un tableau de pointeurs, chacun pointant vers un `ICorDebugValue` objet.</span><span class="sxs-lookup"><span data-stu-id="c0ab4-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c0ab4-108">[out] Pointeur vers le nombre de `ICorDebugValue` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="c0ab4-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="c0ab4-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="c0ab4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0ab4-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c0ab4-110">Requirements</span></span>  
 <span data-ttu-id="c0ab4-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0ab4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0ab4-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0ab4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0ab4-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0ab4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0ab4-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0ab4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ab4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0ab4-115">See Also</span></span>  
    
 
