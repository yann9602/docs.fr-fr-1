---
title: "ICLRMemoryNotificationCallback::OnMemoryNotification, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback.OnMemoryNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 651dcd6380702a392d2dd06cf899ea567b004ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="c25c4-102">ICLRMemoryNotificationCallback::OnMemoryNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="c25c4-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="c25c4-103">Notifie le common language runtime (CLR) de la charge de mémoire sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c25c4-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c25c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c25c4-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c25c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c25c4-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="c25c4-106">[in] Parmi les [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) valeurs, indiquant la sollicitation de la mémoire, l’ordinateur rencontre actuellement.</span><span class="sxs-lookup"><span data-stu-id="c25c4-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c25c4-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c25c4-107">Return Value</span></span>  
  
|<span data-ttu-id="c25c4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c25c4-108">HRESULT</span></span>|<span data-ttu-id="c25c4-109">Description</span><span class="sxs-lookup"><span data-stu-id="c25c4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c25c4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c25c4-110">S_OK</span></span>|<span data-ttu-id="c25c4-111">`OnMemoryNotification`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c25c4-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="c25c4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c25c4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c25c4-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="c25c4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c25c4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c25c4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c25c4-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c25c4-115">The call timed out.</span></span>|  
|<span data-ttu-id="c25c4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c25c4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c25c4-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c25c4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c25c4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c25c4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c25c4-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="c25c4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c25c4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c25c4-120">E_FAIL</span></span>|<span data-ttu-id="c25c4-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c25c4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c25c4-122">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c25c4-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c25c4-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c25c4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c25c4-124">Notes</span><span class="sxs-lookup"><span data-stu-id="c25c4-124">Remarks</span></span>  
 <span data-ttu-id="c25c4-125">Le CLR enregistre un rappel à `OnMemoryNotification` à l’aide d’un appel à la [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="c25c4-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="c25c4-126">Le runtime utilise les informations retournées dans le rappel pour libérer de la mémoire lors de l’hôte indique que la mémoire ressources sont faibles.</span><span class="sxs-lookup"><span data-stu-id="c25c4-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c25c4-127">Les appels à `OnMemoryNotification` jamais bloquer.</span><span class="sxs-lookup"><span data-stu-id="c25c4-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="c25c4-128">Ils retournent toujours immédiatement.</span><span class="sxs-lookup"><span data-stu-id="c25c4-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c25c4-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c25c4-129">Requirements</span></span>  
 <span data-ttu-id="c25c4-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c25c4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c25c4-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c25c4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c25c4-132">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c25c4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c25c4-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c25c4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25c4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c25c4-134">See Also</span></span>  
 [<span data-ttu-id="c25c4-135">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="c25c4-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="c25c4-136">RegisterMemoryNotificationCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="c25c4-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="c25c4-137">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c25c4-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
