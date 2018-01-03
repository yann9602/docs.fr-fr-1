---
title: ICorDebugMemoryBuffer, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98703b07f6601307b5f26aa14b2faf67f8823be5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="beaf6-102">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="beaf6-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="beaf6-103">Représente une mémoire tampon en mémoire.</span><span class="sxs-lookup"><span data-stu-id="beaf6-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="beaf6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="beaf6-104">Methods</span></span>  
  
|<span data-ttu-id="beaf6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="beaf6-105">Method</span></span>|<span data-ttu-id="beaf6-106">Description</span><span class="sxs-lookup"><span data-stu-id="beaf6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="beaf6-107">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="beaf6-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="beaf6-108">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="beaf6-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="beaf6-109">GetStartAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="beaf6-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="beaf6-110">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="beaf6-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beaf6-111">Notes</span><span class="sxs-lookup"><span data-stu-id="beaf6-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="beaf6-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="beaf6-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="beaf6-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="beaf6-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beaf6-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="beaf6-114">Requirements</span></span>  
 <span data-ttu-id="beaf6-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beaf6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beaf6-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="beaf6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="beaf6-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beaf6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beaf6-118">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beaf6-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beaf6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="beaf6-119">See Also</span></span>  
 [<span data-ttu-id="beaf6-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="beaf6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="beaf6-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="beaf6-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
