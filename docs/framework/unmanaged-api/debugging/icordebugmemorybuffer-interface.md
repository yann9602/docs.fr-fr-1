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
ms.openlocfilehash: 80002d064c48a90236a64a3d0a56fab5877cf411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="70eed-102">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="70eed-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="70eed-103">Représente une mémoire tampon en mémoire.</span><span class="sxs-lookup"><span data-stu-id="70eed-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70eed-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="70eed-104">Methods</span></span>  
  
|<span data-ttu-id="70eed-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="70eed-105">Method</span></span>|<span data-ttu-id="70eed-106">Description</span><span class="sxs-lookup"><span data-stu-id="70eed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70eed-107">GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="70eed-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="70eed-108">Obtient la taille de la mémoire tampon en octets.</span><span class="sxs-lookup"><span data-stu-id="70eed-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="70eed-109">GetStartAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="70eed-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="70eed-110">Obtient l'adresse de départ de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="70eed-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70eed-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="70eed-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70eed-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="70eed-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="70eed-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="70eed-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70eed-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="70eed-114">Requirements</span></span>  
 <span data-ttu-id="70eed-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70eed-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70eed-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70eed-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70eed-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70eed-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70eed-118">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70eed-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70eed-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70eed-119">See Also</span></span>  
 [<span data-ttu-id="70eed-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="70eed-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="70eed-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="70eed-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
