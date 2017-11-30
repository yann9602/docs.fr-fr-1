---
title: "IHostTaskManager::SetCLRTaskManager, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetCLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ec0d515ad4c0bc21e1036f20f17bf168d7af79d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="fefc8-102">IHostTaskManager::SetCLRTaskManager, méthode</span><span class="sxs-lookup"><span data-stu-id="fefc8-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="fefc8-103">Fournit à l’hôte avec un pointeur d’interface vers un [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implémentée par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fefc8-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fefc8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fefc8-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fefc8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fefc8-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="fefc8-106">[in] Un pointeur vers un `ICLRTaskManager` instance implémentée par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="fefc8-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fefc8-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fefc8-107">Return Value</span></span>  
  
|<span data-ttu-id="fefc8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fefc8-108">HRESULT</span></span>|<span data-ttu-id="fefc8-109">Description</span><span class="sxs-lookup"><span data-stu-id="fefc8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fefc8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fefc8-110">S_OK</span></span>|<span data-ttu-id="fefc8-111">`SetCLRTaskManager`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="fefc8-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="fefc8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fefc8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fefc8-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="fefc8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fefc8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fefc8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fefc8-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="fefc8-115">The call timed out.</span></span>|  
|<span data-ttu-id="fefc8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fefc8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fefc8-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="fefc8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fefc8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fefc8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fefc8-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="fefc8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fefc8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fefc8-120">E_FAIL</span></span>|<span data-ttu-id="fefc8-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fefc8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fefc8-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fefc8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fefc8-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fefc8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fefc8-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="fefc8-124">Remarks</span></span>  
 <span data-ttu-id="fefc8-125">Le runtime appelle `SetCLRTaskManager` pour fournir l’hôte avec un pointeur d’interface vers un `ICLRTaskManager` instance.</span><span class="sxs-lookup"><span data-stu-id="fefc8-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fefc8-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fefc8-126">Requirements</span></span>  
 <span data-ttu-id="fefc8-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fefc8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fefc8-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fefc8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fefc8-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fefc8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fefc8-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fefc8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefc8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fefc8-131">See Also</span></span>  
 [<span data-ttu-id="fefc8-132">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="fefc8-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="fefc8-133">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="fefc8-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="fefc8-134">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="fefc8-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="fefc8-135">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="fefc8-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
