---
title: "ICorDebugBreakpointEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpointEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0be36669678d33a73809c6be95563321f754697c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="bfcf4-102">ICorDebugBreakpointEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="bfcf4-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="bfcf4-103">Obtient le nombre spécifié d’instances de ICorDebugBreakpoint à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="bfcf4-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfcf4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfcf4-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfcf4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bfcf4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bfcf4-106">[in] Le nombre de `ICorDebugBreakpoint` instances doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="bfcf4-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="bfcf4-107">[out] Un tableau de pointeurs, chacun pointant vers un `ICorDebugBreakpoint` objet qui représente un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="bfcf4-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bfcf4-108">[out] Un pointeur vers le nombre de `ICorDebugBreakpoint` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="bfcf4-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="bfcf4-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="bfcf4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfcf4-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bfcf4-110">Requirements</span></span>  
 <span data-ttu-id="bfcf4-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfcf4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfcf4-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfcf4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfcf4-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfcf4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfcf4-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfcf4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
