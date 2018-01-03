---
title: ICorDebugLoadedModule (interface)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cc7a36deb7c81ccf67427b833dead7127619b39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="0e95f-102">ICorDebugLoadedModule (interface)</span><span class="sxs-lookup"><span data-stu-id="0e95f-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="0e95f-103">Fournit des informations sur un module chargé.</span><span class="sxs-lookup"><span data-stu-id="0e95f-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e95f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0e95f-104">Methods</span></span>  
  
|<span data-ttu-id="0e95f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0e95f-105">Method</span></span>|<span data-ttu-id="0e95f-106">Description</span><span class="sxs-lookup"><span data-stu-id="0e95f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e95f-107">GetBaseAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="0e95f-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="0e95f-108">Obtient l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="0e95f-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="0e95f-109">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="0e95f-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="0e95f-110">Obtient le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="0e95f-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="0e95f-111">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="0e95f-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="0e95f-112">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="0e95f-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e95f-113">Notes</span><span class="sxs-lookup"><span data-stu-id="0e95f-113">Remarks</span></span>  
 <span data-ttu-id="0e95f-114">L'interface `ICorDebugLoadedModule` est implémentée par un débogueur et est utilisée par les interfaces de débogage du CLR pour obtenir des informations sur le module chargé à partir du débogueur.</span><span class="sxs-lookup"><span data-stu-id="0e95f-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e95f-115">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0e95f-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0e95f-116">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="0e95f-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e95f-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e95f-117">Requirements</span></span>  
 <span data-ttu-id="0e95f-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e95f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e95f-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e95f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e95f-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e95f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e95f-121">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e95f-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e95f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e95f-122">See Also</span></span>  
 [<span data-ttu-id="0e95f-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0e95f-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0e95f-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="0e95f-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
