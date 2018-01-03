---
title: "ICorDebug::Terminate, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.Terminate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e416f8ea20bde49a1c1cdb5d61bc4a6bfbce7913
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="3d4be-102">ICorDebug::Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="3d4be-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="3d4be-103">Met fin à la `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="3d4be-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d4be-104">`Terminate`ne doit pas être appelé qu’une [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) rappel a été reçu pour tous les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="3d4be-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4be-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d4be-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3d4be-106">Notes</span><span class="sxs-lookup"><span data-stu-id="3d4be-106">Remarks</span></span>  
 <span data-ttu-id="3d4be-107">`Terminate`doit être appelé lorsque le `ICorDebug` objet n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3d4be-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d4be-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3d4be-108">Requirements</span></span>  
 <span data-ttu-id="3d4be-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d4be-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d4be-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d4be-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d4be-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d4be-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d4be-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d4be-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4be-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d4be-113">See Also</span></span>  
 [<span data-ttu-id="3d4be-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="3d4be-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
