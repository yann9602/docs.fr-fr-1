---
title: ICorDebugStaticFieldSymbol, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b747d2d43fd7ff4dc901dff14277dbce9606497f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="59260-102">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="59260-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="59260-103">Représente les informations sur les symboles de débogage pour un champ static.</span><span class="sxs-lookup"><span data-stu-id="59260-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59260-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="59260-104">Methods</span></span>  
  
|<span data-ttu-id="59260-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="59260-105">Method</span></span>|<span data-ttu-id="59260-106">Description</span><span class="sxs-lookup"><span data-stu-id="59260-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59260-107">GetAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="59260-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="59260-108">Obtient l’adresse du champ static.</span><span class="sxs-lookup"><span data-stu-id="59260-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="59260-109">GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="59260-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="59260-110">Obtient le nom du champ static.</span><span class="sxs-lookup"><span data-stu-id="59260-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="59260-111">GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="59260-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="59260-112">Obtient la taille en octets du champ static.</span><span class="sxs-lookup"><span data-stu-id="59260-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59260-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="59260-113">Remarks</span></span>  
 <span data-ttu-id="59260-114">L'interface `ICorDebugStaticFieldSymbol` est utilisée pour récupérer les informations sur les symboles de débogage pour un champ statique.</span><span class="sxs-lookup"><span data-stu-id="59260-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59260-115">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="59260-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="59260-116">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="59260-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59260-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="59260-117">Requirements</span></span>  
 <span data-ttu-id="59260-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59260-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59260-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59260-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59260-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59260-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59260-121">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59260-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59260-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59260-122">See Also</span></span>  
 [<span data-ttu-id="59260-123">Icordebuginstancefieldsymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="59260-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="59260-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="59260-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="59260-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="59260-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
