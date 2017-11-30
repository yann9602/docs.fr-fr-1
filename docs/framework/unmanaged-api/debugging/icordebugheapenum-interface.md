---
title: ICorDebugHeapEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum
helpviewer_keywords: ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbc97aec2fc9758df17767188c6b4d044b5016fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="00622-102">ICorDebugHeapEnum, interface</span><span class="sxs-lookup"><span data-stu-id="00622-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="00622-103">Fournit un énumérateur pour les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="00622-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="00622-104">Cette interface est une sous-classe de l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="00622-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00622-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="00622-105">Methods</span></span>  
  
|<span data-ttu-id="00622-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="00622-106">Method</span></span>|<span data-ttu-id="00622-107">Description</span><span class="sxs-lookup"><span data-stu-id="00622-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00622-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="00622-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="00622-109">Obtient le nombre spécifié de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances qui contiennent des informations sur les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="00622-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00622-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="00622-110">Remarks</span></span>  
 <span data-ttu-id="00622-111">Le `ICorDebugHeapEnum` interface implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="00622-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="00622-112">Un `ICorDebugHeapEnum` instance est remplie avec [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances en appelant le [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="00622-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="00622-113">Chaque [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance dans la collection représente un objet dynamique sur le tas ou un objet qui n’est pas associé à une racine par n’importe quel objet, mais n’a pas encore été collecté par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="00622-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="00622-114">Le [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objets de la collection peuvent être énumérés en appelant le [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="00622-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00622-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="00622-115">Requirements</span></span>  
 <span data-ttu-id="00622-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00622-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00622-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00622-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00622-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00622-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00622-119">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00622-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00622-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00622-120">See Also</span></span>  
 [<span data-ttu-id="00622-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="00622-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
