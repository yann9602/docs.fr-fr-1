---
title: ICorDebugBlockingObjectEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum
helpviewer_keywords: ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b62da4047029881ddffff5faee9f06072407bfc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="9ab09-102">ICorDebugBlockingObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="9ab09-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="9ab09-103">Fournit un énumérateur pour une liste de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span><span class="sxs-lookup"><span data-stu-id="9ab09-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="9ab09-104">Cette interface est une sous-classe de l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="9ab09-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ab09-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9ab09-105">Methods</span></span>  
  
|<span data-ttu-id="9ab09-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="9ab09-106">Method</span></span>|<span data-ttu-id="9ab09-107">Description</span><span class="sxs-lookup"><span data-stu-id="9ab09-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ab09-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="9ab09-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="9ab09-109">Énumère une liste de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span><span class="sxs-lookup"><span data-stu-id="9ab09-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ab09-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ab09-110">Remarks</span></span>  
 <span data-ttu-id="9ab09-111">Chaque structure `CorDebugBlockingObject` représente un objet qui bloque un thread.</span><span class="sxs-lookup"><span data-stu-id="9ab09-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ab09-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="9ab09-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ab09-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9ab09-113">Requirements</span></span>  
 <span data-ttu-id="9ab09-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ab09-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ab09-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ab09-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ab09-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ab09-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ab09-117">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ab09-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab09-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ab09-118">See Also</span></span>  
 [<span data-ttu-id="9ab09-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9ab09-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9ab09-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="9ab09-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
