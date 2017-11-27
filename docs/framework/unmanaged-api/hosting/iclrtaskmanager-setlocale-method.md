---
title: "ICLRTaskManager::SetLocale, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.SetLocale
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 736e2ef5490aa9185654a6cdf677579b5f30c1e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="9c21f-102">ICLRTaskManager::SetLocale, méthode</span><span class="sxs-lookup"><span data-stu-id="9c21f-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="9c21f-103">Notifie le common language runtime (CLR) que l’hôte a modifié la valeur de l’identificateur de paramètres régionaux (qui correspond à la culture géographique et la langue) sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9c21f-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c21f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c21f-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c21f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c21f-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="9c21f-106">[in] La valeur d’identificateur de paramètres régionaux qui mappe à la culture géographique qui vient d’être attribué et la langue.</span><span class="sxs-lookup"><span data-stu-id="9c21f-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c21f-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9c21f-107">Return Value</span></span>  
  
|<span data-ttu-id="9c21f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c21f-108">HRESULT</span></span>|<span data-ttu-id="9c21f-109">Description</span><span class="sxs-lookup"><span data-stu-id="9c21f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c21f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c21f-110">S_OK</span></span>|<span data-ttu-id="9c21f-111">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9c21f-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="9c21f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c21f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c21f-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="9c21f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c21f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c21f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c21f-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9c21f-115">The call timed out.</span></span>|  
|<span data-ttu-id="9c21f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c21f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c21f-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9c21f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c21f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c21f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c21f-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="9c21f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c21f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c21f-120">E_FAIL</span></span>|<span data-ttu-id="9c21f-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9c21f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c21f-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9c21f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c21f-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9c21f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c21f-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="9c21f-124">Remarks</span></span>  
 <span data-ttu-id="9c21f-125">`SetLocale`possibilité d’exécuter des mécanismes que peut-être pour la synchronisation des paramètres régionaux donne à l’hôte.</span><span class="sxs-lookup"><span data-stu-id="9c21f-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c21f-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9c21f-126">Requirements</span></span>  
 <span data-ttu-id="9c21f-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c21f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c21f-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c21f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c21f-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c21f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c21f-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c21f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c21f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c21f-131">See Also</span></span>  
 [<span data-ttu-id="9c21f-132">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="9c21f-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="9c21f-133">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="9c21f-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9c21f-134">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="9c21f-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="9c21f-135">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="9c21f-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
