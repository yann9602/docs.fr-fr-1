---
title: "ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7de3622498e8417a961e0d4708c53527a833ef2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="b623b-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)</span><span class="sxs-lookup"><span data-stu-id="b623b-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="b623b-103">[Prise en charge dans [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="b623b-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="b623b-104">Active ou désactive certains types de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) rappels d’exception.</span><span class="sxs-lookup"><span data-stu-id="b623b-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b623b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b623b-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b623b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b623b-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="b623b-107">[in]</span><span class="sxs-lookup"><span data-stu-id="b623b-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b623b-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="b623b-108">Remarks</span></span>  
 <span data-ttu-id="b623b-109">Si la valeur de `enableExceptionsOutsideOfJMC` est `false` :</span><span class="sxs-lookup"><span data-stu-id="b623b-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="b623b-110">Une exception DEBUG_EXCEPTION_FIRST_CHANCE n’entraîne pas un rappel au débogueur.</span><span class="sxs-lookup"><span data-stu-id="b623b-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="b623b-111">Une exception DEBUG_EXCEPTION_CATCH_HANDLER_FOUND n’entraîne pas un rappel au débogueur si l’exception s’échappe jamais dans le code utilisateur (autrement dit, le chemin d’origine vers un gestionnaire d’exceptions n’a aucune méthode marquée JustMyCode ou JMC).</span><span class="sxs-lookup"><span data-stu-id="b623b-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="b623b-112">La valeur par défaut de `enableExceptionsOutsideOfJMC` est `true`.</span><span class="sxs-lookup"><span data-stu-id="b623b-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b623b-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b623b-113">Requirements</span></span>  
 <span data-ttu-id="b623b-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b623b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b623b-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b623b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b623b-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b623b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b623b-117">**Versions du .NET framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b623b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b623b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b623b-118">See Also</span></span>  
 [<span data-ttu-id="b623b-119">Icordebugprocess8, Interface</span><span class="sxs-lookup"><span data-stu-id="b623b-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [<span data-ttu-id="b623b-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b623b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
