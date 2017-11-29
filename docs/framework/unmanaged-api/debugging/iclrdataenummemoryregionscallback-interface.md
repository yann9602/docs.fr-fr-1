---
title: ICLRDataEnumMemoryRegionsCallback, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegionsCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords: ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40e51bfc176d8be6b008bc4274c0933253d7be3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="9d15d-102">ICLRDataEnumMemoryRegionsCallback, interface</span><span class="sxs-lookup"><span data-stu-id="9d15d-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="9d15d-103">Fournit une méthode de rappel pour [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) pour signaler au débogueur le résultat d’une tentative d’énumération d’une région spécifiée de mémoire.</span><span class="sxs-lookup"><span data-stu-id="9d15d-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d15d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9d15d-104">Methods</span></span>  
  
|<span data-ttu-id="9d15d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9d15d-105">Method</span></span>|<span data-ttu-id="9d15d-106">Description</span><span class="sxs-lookup"><span data-stu-id="9d15d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d15d-107">EnumMemoryRegion (méthode)</span><span class="sxs-lookup"><span data-stu-id="9d15d-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="9d15d-108">Appelé par `ICLRDataEnumMemoryRegions::EnumMemoryRegions` pour signaler au débogueur le résultat d’une tentative d’énumération d’une région spécifiée de mémoire.</span><span class="sxs-lookup"><span data-stu-id="9d15d-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d15d-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9d15d-109">Requirements</span></span>  
 <span data-ttu-id="9d15d-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d15d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d15d-111">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9d15d-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9d15d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d15d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d15d-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d15d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d15d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d15d-114">See Also</span></span>  
 [<span data-ttu-id="9d15d-115">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9d15d-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
