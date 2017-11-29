---
title: "ICorDebugProcessEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcessEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2628a6d2a93c66531acfbc20acff560f623854fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="cc7fd-102">ICorDebugProcessEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="cc7fd-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="cc7fd-103">Obtient le nombre spécifié d’instances de ICorDebugProcess à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="cc7fd-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc7fd-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc7fd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc7fd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="cc7fd-106">[in] Le nombre de `ICorDebugProcess` instances doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="cc7fd-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processess`  
 <span data-ttu-id="cc7fd-107">[out] Un tableau de pointeurs, chacun pointant vers un `ICorDebugProcess` objet qui représente un processus.</span><span class="sxs-lookup"><span data-stu-id="cc7fd-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="cc7fd-108">[out] Pointeur vers le nombre de `ICorDebugProcess` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="cc7fd-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="cc7fd-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="cc7fd-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc7fd-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cc7fd-110">Requirements</span></span>  
 <span data-ttu-id="cc7fd-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7fd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7fd-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc7fd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc7fd-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc7fd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc7fd-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
