---
title: "ICorDebugChainEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3d6d587b1a249d08ffb250453fb9c007dc3df3e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="4b90c-102">ICorDebugChainEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="4b90c-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="4b90c-103">Obtient le nombre spécifié d’instances ICorDebugChain à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="4b90c-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b90c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b90c-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b90c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4b90c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4b90c-106">[in] Le nombre de `ICorDebugChain` instances doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="4b90c-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="4b90c-107">[out] Un tableau de pointeurs, chacun pointant vers un `ICorDebugChain` objet qui représente une chaîne.</span><span class="sxs-lookup"><span data-stu-id="4b90c-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4b90c-108">[out] Un pointeur vers le nombre de `ICorDebugChain` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="4b90c-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="4b90c-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="4b90c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b90c-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4b90c-110">Requirements</span></span>  
 <span data-ttu-id="4b90c-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b90c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b90c-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b90c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b90c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b90c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b90c-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b90c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>