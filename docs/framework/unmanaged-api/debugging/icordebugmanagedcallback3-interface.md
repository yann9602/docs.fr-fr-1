---
title: ICorDebugManagedCallback3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3
helpviewer_keywords: ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2f24cc8fbd8533ef6717bc1dcd1baab0ea9ab45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="4bbe9-102">ICorDebugManagedCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="4bbe9-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="4bbe9-103">Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="4bbe9-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4bbe9-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4bbe9-104">Methods</span></span>  
  
|<span data-ttu-id="4bbe9-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4bbe9-105">Method</span></span>|<span data-ttu-id="4bbe9-106">Description</span><span class="sxs-lookup"><span data-stu-id="4bbe9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4bbe9-107">CustomNotification (méthode)</span><span class="sxs-lookup"><span data-stu-id="4bbe9-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="4bbe9-108">Indique qu’une notification de débogueur personnalisée active a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="4bbe9-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bbe9-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="4bbe9-109">Remarks</span></span>  
 <span data-ttu-id="4bbe9-110">Cette interface est une extension logique de la [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) et [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span><span class="sxs-lookup"><span data-stu-id="4bbe9-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bbe9-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="4bbe9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bbe9-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4bbe9-112">Requirements</span></span>  
 <span data-ttu-id="4bbe9-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bbe9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bbe9-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bbe9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bbe9-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bbe9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bbe9-116">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bbe9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbe9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bbe9-117">See Also</span></span>  
 [<span data-ttu-id="4bbe9-118">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="4bbe9-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 [<span data-ttu-id="4bbe9-119">ICorDebugManagedCallback2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="4bbe9-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="4bbe9-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4bbe9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4bbe9-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="4bbe9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
