---
title: "ICorDebugProcess5::GetGCHeapInformation, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetGCHeapInformation
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da423914d8af20c0f942d53ed6ac9f34ace01ca9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="fca04-102">ICorDebugProcess5::GetGCHeapInformation, méthode</span><span class="sxs-lookup"><span data-stu-id="fca04-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="fca04-103">Fournit des informations générales sur le tas de garbage collection, notamment s’il est actuellement énumérable.</span><span class="sxs-lookup"><span data-stu-id="fca04-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fca04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fca04-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fca04-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fca04-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="fca04-106">[out] Un pointeur vers un [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) valeur qui fournit des informations générales sur le tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="fca04-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fca04-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="fca04-107">Remarks</span></span>  
 <span data-ttu-id="fca04-108">Le `ICorDebugProcess5::GetGCHeapInformation` méthode doit être appelée avant l’énumération du tas ou régions individuelles de segment de mémoire pour vous assurer que les structures dans le processus de garbage collection sont valides.</span><span class="sxs-lookup"><span data-stu-id="fca04-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="fca04-109">Tas de garbage collection ne peut pas être parcouru pendant une collection est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="fca04-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="fca04-110">Dans le cas contraire, l’énumération peut capturer des structures de garbage collection qui ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="fca04-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fca04-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fca04-111">Requirements</span></span>  
 <span data-ttu-id="fca04-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fca04-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fca04-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fca04-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fca04-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fca04-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fca04-115">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fca04-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca04-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fca04-116">See Also</span></span>  
 [<span data-ttu-id="fca04-117">Icordebugprocess5, Interface</span><span class="sxs-lookup"><span data-stu-id="fca04-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="fca04-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fca04-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
