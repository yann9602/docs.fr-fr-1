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
ms.openlocfilehash: b18bb6222296c5e8875f983d47118f938a54bcc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="8c932-102">ICorDebug::Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="8c932-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="8c932-103">Met fin à la `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="8c932-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c932-104">`Terminate`ne doit pas être appelé qu’une [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) rappel a été reçu pour tous les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="8c932-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c932-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c932-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8c932-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="8c932-106">Remarks</span></span>  
 <span data-ttu-id="8c932-107">`Terminate`doit être appelé lorsque le `ICorDebug` objet n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8c932-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c932-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8c932-108">Requirements</span></span>  
 <span data-ttu-id="8c932-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c932-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c932-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c932-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c932-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c932-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c932-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c932-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c932-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c932-113">See Also</span></span>  
 [<span data-ttu-id="8c932-114">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="8c932-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
