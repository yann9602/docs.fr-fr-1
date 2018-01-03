---
title: ICorDebugCode3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3
helpviewer_keywords: ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a89bc2b516f87a4deb7ccb794b5ae0352d6a8efc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="ebf9c-102">ICorDebugCode3, interface</span><span class="sxs-lookup"><span data-stu-id="ebf9c-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="ebf9c-103">Fournit une méthode qui étend les fonctionnalités « ICorDebugCode » et « ICorDebugCode2 » pour fournir des informations sur une valeur de retournée managée.</span><span class="sxs-lookup"><span data-stu-id="ebf9c-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebf9c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ebf9c-104">Methods</span></span>  
  
|<span data-ttu-id="ebf9c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ebf9c-105">Method</span></span>|<span data-ttu-id="ebf9c-106">Description</span><span class="sxs-lookup"><span data-stu-id="ebf9c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebf9c-107">GetReturnValueLiveOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="ebf9c-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="ebf9c-108">Pour un offset IL spécifié, obtient les offsets natifs où un point d’arrêt doit être placé afin que le débogueur peut obtenir la valeur de retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="ebf9c-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebf9c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ebf9c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebf9c-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ebf9c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf9c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ebf9c-111">Requirements</span></span>  
 <span data-ttu-id="ebf9c-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf9c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf9c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebf9c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebf9c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebf9c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebf9c-115">**Versions du .NET framework :**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf9c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf9c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebf9c-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="ebf9c-117">ICorDebugILFrame3, interface</span><span class="sxs-lookup"><span data-stu-id="ebf9c-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="ebf9c-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ebf9c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
