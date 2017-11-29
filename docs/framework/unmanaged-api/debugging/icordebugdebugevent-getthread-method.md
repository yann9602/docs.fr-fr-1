---
title: "ICorDebugDebugEvent::GetThread, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13b950545c2c8c8b54d24b932351d80280e1dac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="0a10d-102">ICorDebugDebugEvent::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="0a10d-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="0a10d-103">Obtient le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="0a10d-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a10d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a10d-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a10d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a10d-105">Parameters</span></span>  
 <span data-ttu-id="0a10d-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="0a10d-106">ppThread</span></span>  
 <span data-ttu-id="0a10d-107">[out] Pointeur vers l’adresse d’un objet ICorDebugThread qui représente le thread sur lequel l’événement s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0a10d-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a10d-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="0a10d-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a10d-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0a10d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a10d-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0a10d-110">Requirements</span></span>  
 <span data-ttu-id="0a10d-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a10d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a10d-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a10d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a10d-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a10d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a10d-114">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a10d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a10d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a10d-115">See Also</span></span>  
 [<span data-ttu-id="0a10d-116">Icordebugdebugevent, Interface</span><span class="sxs-lookup"><span data-stu-id="0a10d-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="0a10d-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0a10d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
