---
title: "ICLRTask::Abort, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Abort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e417e329b38c8f57dedf2926c0d6ff02a0170f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="54c43-102">ICLRTask::Abort, méthode</span><span class="sxs-lookup"><span data-stu-id="54c43-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="54c43-103">Demande que le common language runtime (CLR) abandonne la tâche qui en cours [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) représente l’instance.</span><span class="sxs-lookup"><span data-stu-id="54c43-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54c43-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="54c43-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="54c43-105">Return Value</span></span>  
  
|<span data-ttu-id="54c43-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54c43-106">HRESULT</span></span>|<span data-ttu-id="54c43-107">Description</span><span class="sxs-lookup"><span data-stu-id="54c43-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54c43-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="54c43-108">S_OK</span></span>|<span data-ttu-id="54c43-109">`Abort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="54c43-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="54c43-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54c43-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54c43-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="54c43-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54c43-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54c43-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54c43-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="54c43-113">The call timed out.</span></span>|  
|<span data-ttu-id="54c43-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54c43-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54c43-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="54c43-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54c43-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54c43-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54c43-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="54c43-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54c43-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54c43-118">E_FAIL</span></span>|<span data-ttu-id="54c43-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="54c43-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54c43-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="54c43-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54c43-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="54c43-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54c43-122">Notes</span><span class="sxs-lookup"><span data-stu-id="54c43-122">Remarks</span></span>  
 <span data-ttu-id="54c43-123">Le CLR lève une <xref:System.Threading.ThreadAbortException> lorsque l’hôte appelle la méthode `Abort`.</span><span class="sxs-lookup"><span data-stu-id="54c43-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="54c43-124">Il retourne immédiatement après initialisation des informations sur l’exception, sans attendre le code de l’utilisateur, telles que les finaliseurs ou les mécanismes de gestion des exceptions à exécuter.</span><span class="sxs-lookup"><span data-stu-id="54c43-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="54c43-125">Les appels à `Abort` retournent donc rapidement.</span><span class="sxs-lookup"><span data-stu-id="54c43-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54c43-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="54c43-126">Requirements</span></span>  
 <span data-ttu-id="54c43-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54c43-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c43-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54c43-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54c43-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54c43-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54c43-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54c43-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c43-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54c43-131">See Also</span></span>  
 [<span data-ttu-id="54c43-132">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="54c43-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="54c43-133">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="54c43-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="54c43-134">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="54c43-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="54c43-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="54c43-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
