---
title: "ICorDebugFrameEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrameEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2139661621d7ebe2bf20e96b400096393964b89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="2828b-102">ICorDebugFrameEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="2828b-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="2828b-103">Obtient le nombre spécifié d’instances ICorDebugFrame, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="2828b-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2828b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2828b-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2828b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2828b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="2828b-106">[in] Le nombre de `ICorDebugFrame` instances doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="2828b-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="2828b-107">[out] Un tableau de pointeurs, chacun pointant vers un `ICorDebugFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="2828b-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2828b-108">[out] Un pointeur vers le nombre de `ICorDebugFrame` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="2828b-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="2828b-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="2828b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2828b-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2828b-110">Requirements</span></span>  
 <span data-ttu-id="2828b-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2828b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2828b-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2828b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2828b-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2828b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2828b-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2828b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
