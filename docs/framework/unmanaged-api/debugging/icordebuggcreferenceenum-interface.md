---
title: ICorDebugGCReferenceEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum
helpviewer_keywords: ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afe52c3df8f61b234b3c68ee819ba8389593c82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="f9dbb-102">ICorDebugGCReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f9dbb-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="f9dbb-103">Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9dbb-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f9dbb-104">Methods</span></span>  
  
|<span data-ttu-id="f9dbb-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f9dbb-105">Method</span></span>|<span data-ttu-id="f9dbb-106">Description</span><span class="sxs-lookup"><span data-stu-id="f9dbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9dbb-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f9dbb-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="f9dbb-108">Obtient le nombre spécifié de [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances qui contiennent des informations sur les objets qui seront par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9dbb-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f9dbb-109">Remarks</span></span>  
 <span data-ttu-id="f9dbb-110">Le `ICorDebugGCReferenceEnum` interface implémente l’interface « ICorDebugEnum ».</span><span class="sxs-lookup"><span data-stu-id="f9dbb-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="f9dbb-111">Un `ICorDebugGCReferenceEnum` instance est remplie avec [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances en appelant le [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f9dbb-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="f9dbb-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objets peuvent être énumérées en appelant le [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f9dbb-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="f9dbb-113">Le [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) trois types d’objets représentent des objets dans la collection remplie par cette méthode :</span><span class="sxs-lookup"><span data-stu-id="f9dbb-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="f9dbb-114">Objets de toutes les piles managées.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-114">Objects from all managed stacks.</span></span> <span data-ttu-id="f9dbb-115">Cela inclut des références actives dans le code managé, ainsi que les objets créés par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="f9dbb-116">Objets à partir de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-116">Objects from the handle table.</span></span> <span data-ttu-id="f9dbb-117">Cela inclut des références solides (`HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT`) et les variables statiques dans un module.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="f9dbb-118">Objets à partir de la file d’attente du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="f9dbb-119">La file d’attente du finaliseur racines d’objets jusqu'à ce que le finaliseur a exécuté.</span><span class="sxs-lookup"><span data-stu-id="f9dbb-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9dbb-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f9dbb-120">Requirements</span></span>  
 <span data-ttu-id="f9dbb-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9dbb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9dbb-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9dbb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9dbb-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9dbb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9dbb-124">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9dbb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9dbb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9dbb-125">See Also</span></span>  
 [<span data-ttu-id="f9dbb-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f9dbb-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
