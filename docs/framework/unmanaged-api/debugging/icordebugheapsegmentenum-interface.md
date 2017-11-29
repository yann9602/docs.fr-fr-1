---
title: ICorDebugHeapSegmentEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHealRegionEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum
helpviewer_keywords: ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ca82e888ba078fcb8b855f5286bc14f970d64ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="61cdf-102">ICorDebugHeapSegmentEnum, interface</span><span class="sxs-lookup"><span data-stu-id="61cdf-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="61cdf-103">Fournit un énumérateur pour les régions de mémoire du tas managé.</span><span class="sxs-lookup"><span data-stu-id="61cdf-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="61cdf-104">Cette interface est une sous-classe de l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="61cdf-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61cdf-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="61cdf-105">Methods</span></span>  
  
|<span data-ttu-id="61cdf-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="61cdf-106">Method</span></span>|<span data-ttu-id="61cdf-107">Description</span><span class="sxs-lookup"><span data-stu-id="61cdf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61cdf-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="61cdf-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="61cdf-109">Obtient le nombre spécifié de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances qui contiennent des informations sur les zones du tas managé.</span><span class="sxs-lookup"><span data-stu-id="61cdf-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61cdf-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="61cdf-110">Remarks</span></span>  
 <span data-ttu-id="61cdf-111">Le `ICorDebugHeapSegmentEnum` interface implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="61cdf-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="61cdf-112">Un `ICorDebugHeapSegmentEnum` instance est remplie avec [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances en appelant le [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="61cdf-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="61cdf-113">Le [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objets de la collection peuvent être énumérés en appelant le [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="61cdf-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="61cdf-114">Un `ICorDebugHeapSegmentEnum` objet de collection énumère toutes les régions de mémoire qui peuvent contenir des objets gérés, mais il ne garantit pas que les objets gérés qui résident dans ces régions.</span><span class="sxs-lookup"><span data-stu-id="61cdf-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="61cdf-115">Il peut inclure des informations sur les régions de mémoire vide ou réservés.</span><span class="sxs-lookup"><span data-stu-id="61cdf-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61cdf-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="61cdf-116">Requirements</span></span>  
 <span data-ttu-id="61cdf-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61cdf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61cdf-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61cdf-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61cdf-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61cdf-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61cdf-120">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61cdf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cdf-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61cdf-121">See Also</span></span>  
 [<span data-ttu-id="61cdf-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="61cdf-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
