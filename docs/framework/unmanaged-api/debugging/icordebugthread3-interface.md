---
title: ICorDebugThread3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3
helpviewer_keywords: ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed505cacc5286d27bc9a94eaa192dc6b889eb525
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="6fb47-102">ICorDebugThread3, interface</span><span class="sxs-lookup"><span data-stu-id="6fb47-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="6fb47-103">Fournit le point d’entrée pour le [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) et les interfaces correspondantes.</span><span class="sxs-lookup"><span data-stu-id="6fb47-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6fb47-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6fb47-104">Methods</span></span>  
  
|<span data-ttu-id="6fb47-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="6fb47-105">Method</span></span>|<span data-ttu-id="6fb47-106">Description</span><span class="sxs-lookup"><span data-stu-id="6fb47-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6fb47-107">CreateStackWalk (méthode)</span><span class="sxs-lookup"><span data-stu-id="6fb47-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="6fb47-108">Crée un [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objet pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="6fb47-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="6fb47-109">GetActiveInternalFrames (méthode)</span><span class="sxs-lookup"><span data-stu-id="6fb47-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="6fb47-110">Retourne un tableau de frames internes ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objets) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="6fb47-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fb47-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="6fb47-111">Remarks</span></span>  
 <span data-ttu-id="6fb47-112">`ICorDebugThread3`est une extension logique à l’interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="6fb47-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fb47-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="6fb47-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb47-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6fb47-114">Requirements</span></span>  
 <span data-ttu-id="6fb47-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fb47-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb47-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fb47-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fb47-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fb47-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fb47-118">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb47-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb47-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fb47-119">See Also</span></span>  
 [<span data-ttu-id="6fb47-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6fb47-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6fb47-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="6fb47-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
