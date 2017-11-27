---
title: "ICorDebugProcess6::ProcessStateChanged, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 22fe068af577c3c3eb056acae388747f88d3f8df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="e9396-102">ICorDebugProcess6::ProcessStateChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="e9396-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="e9396-103">Notifie [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e9396-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9396-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9396-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9396-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9396-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="e9396-106">[in] Un membre de la [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) énumération</span><span class="sxs-lookup"><span data-stu-id="e9396-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9396-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="e9396-107">Remarks</span></span>  
 <span data-ttu-id="e9396-108">Le débogueur appelle cette méthode pour notifier [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e9396-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9396-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e9396-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9396-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e9396-110">Requirements</span></span>  
 <span data-ttu-id="e9396-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9396-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9396-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9396-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9396-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9396-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9396-114">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9396-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9396-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9396-115">See Also</span></span>  
 [<span data-ttu-id="e9396-116">Icordebugprocess6, Interface</span><span class="sxs-lookup"><span data-stu-id="e9396-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="e9396-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e9396-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
