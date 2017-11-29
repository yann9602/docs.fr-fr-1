---
title: ICLRMemoryNotificationCallback, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback
helpviewer_keywords: ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b998f8af2c7f4add3ecbb905928b5956409bf00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="f352b-102">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f352b-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="f352b-103">Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de Win32 `CreateMemoryResourceNotification` (fonction).</span><span class="sxs-lookup"><span data-stu-id="f352b-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f352b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f352b-104">Methods</span></span>  
  
|<span data-ttu-id="f352b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f352b-105">Method</span></span>|<span data-ttu-id="f352b-106">Description</span><span class="sxs-lookup"><span data-stu-id="f352b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f352b-107">OnMemoryNotification (méthode)</span><span class="sxs-lookup"><span data-stu-id="f352b-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="f352b-108">Notifie le common language runtime (CLR) de la charge de mémoire sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f352b-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f352b-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f352b-109">Remarks</span></span>  
 <span data-ttu-id="f352b-110">L’hôte utilise le `ICLRMemoryNotificationCallback` interface pour demander que le CLR libère des ressources mémoire.</span><span class="sxs-lookup"><span data-stu-id="f352b-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f352b-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f352b-111">Requirements</span></span>  
 <span data-ttu-id="f352b-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f352b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f352b-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f352b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f352b-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f352b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f352b-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f352b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f352b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f352b-116">See Also</span></span>  
 [<span data-ttu-id="f352b-117">IHostMemoryManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="f352b-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="f352b-118">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f352b-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
