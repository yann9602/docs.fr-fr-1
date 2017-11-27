---
title: "ICorDebugCode::GetILToNativeMapping, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetILToNativeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54937e8d5d7a2e345ebcbccadbc592b12e3ee9b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="3dc37-102">ICorDebugCode::GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="3dc37-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="3dc37-103">Obtient un tableau d’instances de « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent les mappages à partir de Microsoft intermediate language (MSIL) aux offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="3dc37-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dc37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dc37-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3dc37-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3dc37-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="3dc37-106">[in] Taille du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="3dc37-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="3dc37-107">[out] Un pointeur vers le nombre réel d’éléments retournés dans le `map` tableau.</span><span class="sxs-lookup"><span data-stu-id="3dc37-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="3dc37-108">[out] Un tableau de `COR_DEBUG_IL_TO_NATIVE_MAP` structures, chacune représentant un mappage d’un offset MSIL à un offset natif.</span><span class="sxs-lookup"><span data-stu-id="3dc37-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="3dc37-109">Il n’existe aucun classement dans le tableau des éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="3dc37-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dc37-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="3dc37-110">Remarks</span></span>  
 <span data-ttu-id="3dc37-111">Le `GetILToNativeMapping` méthode retourne des résultats significatifs uniquement si cette instance de « ICorDebugCode » représente le code natif qui a été compilé à partir du code MSIL juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="3dc37-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dc37-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3dc37-112">Requirements</span></span>  
 <span data-ttu-id="3dc37-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dc37-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dc37-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dc37-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dc37-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dc37-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dc37-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dc37-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc37-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dc37-117">See Also</span></span>  
 [<span data-ttu-id="3dc37-118">ICorDebugCode Interface1</span><span class="sxs-lookup"><span data-stu-id="3dc37-118">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
