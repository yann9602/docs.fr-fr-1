---
title: "EMemoryAvailable, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryAvailable
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryAvailable
helpviewer_keywords: EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 596b174fa4ebac7e54e2f6b5f3ed044686fa515f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="1fec8-102">EMemoryAvailable, énumération</span><span class="sxs-lookup"><span data-stu-id="1fec8-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="1fec8-103">Contient des valeurs qui indiquent la quantité de mémoire physique disponible sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1fec8-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="1fec8-104">Ces valeurs mappent logiquement aux événements de haute et basse mémoire retournée à partir de la `CreateMemoryResourceNotification` fonction dans l’API Win32.</span><span class="sxs-lookup"><span data-stu-id="1fec8-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fec8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fec8-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="1fec8-106">Membres</span><span class="sxs-lookup"><span data-stu-id="1fec8-106">Members</span></span>  
  
|<span data-ttu-id="1fec8-107">Membre</span><span class="sxs-lookup"><span data-stu-id="1fec8-107">Member</span></span>|<span data-ttu-id="1fec8-108">Description</span><span class="sxs-lookup"><span data-stu-id="1fec8-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="1fec8-109">Beaucoup de mémoire physique est disponible.</span><span class="sxs-lookup"><span data-stu-id="1fec8-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="1fec8-110">Très peu de mémoire physique est disponible.</span><span class="sxs-lookup"><span data-stu-id="1fec8-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="1fec8-111">La mémoire physique disponible est neutre.</span><span class="sxs-lookup"><span data-stu-id="1fec8-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fec8-112">Notes</span><span class="sxs-lookup"><span data-stu-id="1fec8-112">Remarks</span></span>  
 <span data-ttu-id="1fec8-113">Cette valeur est passée par l’hôte pour le common language runtime (CLR) en utilisant un appel à la [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="1fec8-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fec8-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1fec8-114">Requirements</span></span>  
 <span data-ttu-id="1fec8-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fec8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fec8-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1fec8-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1fec8-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1fec8-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fec8-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fec8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fec8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fec8-119">See Also</span></span>  
 [<span data-ttu-id="1fec8-120">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="1fec8-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
