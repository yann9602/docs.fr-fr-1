---
title: "IHostTask::Alert, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Alert
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf48d3decd071c4c0f483476b885fc023b466f3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="ea395-102">IHostTask::Alert, méthode</span><span class="sxs-lookup"><span data-stu-id="ea395-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="ea395-103">Demande que l’hôte réactive la tâche représentée par le [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) de l’instance, donc la tâche peut être annulée.</span><span class="sxs-lookup"><span data-stu-id="ea395-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea395-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea395-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ea395-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ea395-105">Return Value</span></span>  
  
|<span data-ttu-id="ea395-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea395-106">HRESULT</span></span>|<span data-ttu-id="ea395-107">Description</span><span class="sxs-lookup"><span data-stu-id="ea395-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea395-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea395-108">S_OK</span></span>|<span data-ttu-id="ea395-109">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ea395-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="ea395-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea395-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea395-111">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="ea395-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea395-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea395-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea395-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ea395-113">The call timed out.</span></span>|  
|<span data-ttu-id="ea395-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea395-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea395-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ea395-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea395-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea395-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea395-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="ea395-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea395-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea395-118">E_FAIL</span></span>|<span data-ttu-id="ea395-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ea395-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea395-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ea395-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea395-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea395-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea395-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="ea395-122">Remarks</span></span>  
 <span data-ttu-id="ea395-123">Le CLR appelle la `Alert` méthode lors de la <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> est appelée à partir du code utilisateur, ou lorsque le <xref:System.AppDomain> associé en cours <xref:System.Threading.Thread> s’arrête.</span><span class="sxs-lookup"><span data-stu-id="ea395-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="ea395-124">L’hôte doit retourner immédiatement, car l’appel est effectué de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ea395-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="ea395-125">Si l’ordinateur hôte ne peut pas alerter immédiatement la tâche, il doit se réveiller la prochaine fois qu’il entre dans un état dans lequel il peut être alerté.</span><span class="sxs-lookup"><span data-stu-id="ea395-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea395-126">`Alert`affecte uniquement les tâches auxquelles le runtime a passé un [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeur WAIT_ALERTABLE aux méthodes telles que [joindre](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="ea395-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea395-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ea395-127">Requirements</span></span>  
 <span data-ttu-id="ea395-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea395-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea395-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea395-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea395-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea395-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea395-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea395-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea395-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea395-132">See Also</span></span>  
 [<span data-ttu-id="ea395-133">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="ea395-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ea395-134">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="ea395-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ea395-135">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="ea395-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ea395-136">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="ea395-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
