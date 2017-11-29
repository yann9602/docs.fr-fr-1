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
ms.openlocfilehash: ee60d052c65df64b1a753166b301ba0012cdc8e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="37a90-102">ICorDebugCode3, interface</span><span class="sxs-lookup"><span data-stu-id="37a90-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="37a90-103">Fournit une méthode qui étend les fonctionnalités « ICorDebugCode » et « ICorDebugCode2 » pour fournir des informations sur une valeur de retournée managée.</span><span class="sxs-lookup"><span data-stu-id="37a90-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37a90-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="37a90-104">Methods</span></span>  
  
|<span data-ttu-id="37a90-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="37a90-105">Method</span></span>|<span data-ttu-id="37a90-106">Description</span><span class="sxs-lookup"><span data-stu-id="37a90-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37a90-107">Getreturnvalueliveoffset, méthode</span><span class="sxs-lookup"><span data-stu-id="37a90-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="37a90-108">Pour un offset IL spécifié, obtient les offsets natifs où un point d’arrêt doit être placé afin que le débogueur peut obtenir la valeur de retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="37a90-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37a90-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="37a90-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37a90-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="37a90-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37a90-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="37a90-111">Requirements</span></span>  
 <span data-ttu-id="37a90-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37a90-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37a90-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37a90-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37a90-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37a90-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37a90-115">**Versions du .NET framework :**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37a90-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a90-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37a90-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="37a90-117">Icordebugilframe3, Interface</span><span class="sxs-lookup"><span data-stu-id="37a90-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="37a90-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="37a90-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
