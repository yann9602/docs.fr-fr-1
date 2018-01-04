---
title: IHostMalloc, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1690f5fe8f1417e6547ed94db8c71f079ebf5e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="f7c80-102">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="f7c80-102">IHostMalloc Interface</span></span>
<span data-ttu-id="f7c80-103">Fournit des méthodes qui permettent le common language runtime (CLR) pour demander des allocations fines à partir du tas via l’hôte.</span><span class="sxs-lookup"><span data-stu-id="f7c80-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7c80-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f7c80-104">Methods</span></span>  
  
|<span data-ttu-id="f7c80-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f7c80-105">Method</span></span>|<span data-ttu-id="f7c80-106">Description</span><span class="sxs-lookup"><span data-stu-id="f7c80-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7c80-107">Alloc, méthode</span><span class="sxs-lookup"><span data-stu-id="f7c80-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="f7c80-108">Demande que l’hôte alloue la quantité de mémoire demandée à partir du tas.</span><span class="sxs-lookup"><span data-stu-id="f7c80-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="f7c80-109">DebugAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="f7c80-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="f7c80-110">Demande que l’hôte alloue la quantité de mémoire demandée à partir du tas et enregistre également où la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="f7c80-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="f7c80-111">Free, méthode</span><span class="sxs-lookup"><span data-stu-id="f7c80-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="f7c80-112">Libère la mémoire qui a été allouée à l’aide de la `Alloc` (méthode).</span><span class="sxs-lookup"><span data-stu-id="f7c80-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7c80-113">Notes</span><span class="sxs-lookup"><span data-stu-id="f7c80-113">Remarks</span></span>  
 <span data-ttu-id="f7c80-114">Le CLR obtient un pointeur d’interface vers un `IHostMalloc` instance en appelant le [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f7c80-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c80-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7c80-115">Requirements</span></span>  
 <span data-ttu-id="f7c80-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7c80-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c80-117">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7c80-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7c80-118">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7c80-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7c80-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c80-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c80-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7c80-120">See Also</span></span>  
 [<span data-ttu-id="f7c80-121">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="f7c80-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="f7c80-122">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f7c80-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
