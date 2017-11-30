---
title: "IHostTaskManager::EnterRuntime, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a4c0304047246c912be965d80a26b26ec2344ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="adc4c-102">IHostTaskManager::EnterRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="adc4c-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="adc4c-103">Avertit l’hôte qu’un appel à une méthode non managée, comme un appel de méthode, retourne le contrôle d’exécution pour le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="adc4c-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adc4c-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="adc4c-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="adc4c-105">Return Value</span></span>  
  
|<span data-ttu-id="adc4c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="adc4c-106">HRESULT</span></span>|<span data-ttu-id="adc4c-107">Description</span><span class="sxs-lookup"><span data-stu-id="adc4c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adc4c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="adc4c-108">S_OK</span></span>|<span data-ttu-id="adc4c-109">`EnterRuntime`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="adc4c-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="adc4c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="adc4c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="adc4c-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="adc4c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="adc4c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="adc4c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="adc4c-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="adc4c-113">The call timed out.</span></span>|  
|<span data-ttu-id="adc4c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="adc4c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="adc4c-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="adc4c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="adc4c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="adc4c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="adc4c-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="adc4c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="adc4c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="adc4c-118">E_FAIL</span></span>|<span data-ttu-id="adc4c-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="adc4c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="adc4c-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="adc4c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="adc4c-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="adc4c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="adc4c-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="adc4c-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="adc4c-123">Mémoire était insuffisante pour terminer l’allocation demandée.</span><span class="sxs-lookup"><span data-stu-id="adc4c-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adc4c-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="adc4c-124">Remarks</span></span>  
 <span data-ttu-id="adc4c-125">`EnterRuntime`est appelé pour avertir l’hôte qui une fonction non managée, pour laquelle un appel précédent à la [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) méthode a été effectuée, l’exécution est terminée et retourne le contrôle de l’exécution à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="adc4c-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adc4c-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) est appelé pour avertir l’hôte qui une fonction non managée, pour laquelle un appel précédent à `LeaveRuntime` a été réalisée, effectue un appel dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="adc4c-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adc4c-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="adc4c-127">Requirements</span></span>  
 <span data-ttu-id="adc4c-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adc4c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc4c-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="adc4c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="adc4c-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="adc4c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adc4c-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc4c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc4c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adc4c-132">See Also</span></span>  
 [<span data-ttu-id="adc4c-133">Interopérabilité COM avancée</span><span class="sxs-lookup"><span data-stu-id="adc4c-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="adc4c-134">Guide pratique pour appeler des DLL natives à partir du code managé à l’aide de PInvoke</span><span class="sxs-lookup"><span data-stu-id="adc4c-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="adc4c-135">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="adc4c-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="adc4c-136">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="adc4c-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="adc4c-137">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="adc4c-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="adc4c-138">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="adc4c-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="adc4c-139">LeaveRuntime (méthode)</span><span class="sxs-lookup"><span data-stu-id="adc4c-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
