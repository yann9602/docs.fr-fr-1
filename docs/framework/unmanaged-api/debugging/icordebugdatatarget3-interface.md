---
title: ICorDebugDataTarget3 (interface)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ab94e792265916e29ed24239e25cb5d57d1313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="c9016-102">ICorDebugDataTarget3 (interface)</span><span class="sxs-lookup"><span data-stu-id="c9016-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="c9016-103">Étend logiquement le [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface pour fournir des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="c9016-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="c9016-104">Méthode</span><span class="sxs-lookup"><span data-stu-id="c9016-104">Method</span></span>  
  
|<span data-ttu-id="c9016-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="c9016-105">Method</span></span>|<span data-ttu-id="c9016-106">Description</span><span class="sxs-lookup"><span data-stu-id="c9016-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9016-107">GetLoadedModules (méthode)</span><span class="sxs-lookup"><span data-stu-id="c9016-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="c9016-108">Obtient la liste des modules qui ont été chargés jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="c9016-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9016-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="c9016-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9016-110">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c9016-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c9016-111">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="c9016-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9016-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c9016-112">Requirements</span></span>  
 <span data-ttu-id="c9016-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9016-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9016-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9016-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9016-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9016-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9016-116">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9016-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9016-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9016-117">See Also</span></span>  
 [<span data-ttu-id="c9016-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c9016-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c9016-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="c9016-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
