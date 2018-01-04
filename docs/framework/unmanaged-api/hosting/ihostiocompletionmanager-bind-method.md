---
title: "IHostIoCompletionManager::Bind, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.Bind
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a34de8c04e248d2973e9b27c10da9313db5077ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="04a7e-102">IHostIoCompletionManager::Bind, méthode</span><span class="sxs-lookup"><span data-stu-id="04a7e-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="04a7e-103">Lie le handle spécifié à un port de terminaison d’e/s qui a été créé par un appel précédent à [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="04a7e-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04a7e-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04a7e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04a7e-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="04a7e-106">[in] Le port de terminaison d’e/s auquel lier `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="04a7e-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="04a7e-107">Si la valeur de `hPort` a la valeur null, `hHandle` est lié au port de terminaison d’e/s par défaut.</span><span class="sxs-lookup"><span data-stu-id="04a7e-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="04a7e-108">[in] Le handle de système d’exploitation à lier à `hPort`.</span><span class="sxs-lookup"><span data-stu-id="04a7e-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04a7e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="04a7e-109">Return Value</span></span>  
  
|<span data-ttu-id="04a7e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04a7e-110">HRESULT</span></span>|<span data-ttu-id="04a7e-111">Description</span><span class="sxs-lookup"><span data-stu-id="04a7e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04a7e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="04a7e-112">S_OK</span></span>|<span data-ttu-id="04a7e-113">`Bind`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="04a7e-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="04a7e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04a7e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04a7e-115">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="04a7e-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04a7e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04a7e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04a7e-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="04a7e-117">The call timed out.</span></span>|  
|<span data-ttu-id="04a7e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04a7e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04a7e-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="04a7e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04a7e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04a7e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04a7e-121">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="04a7e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04a7e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04a7e-122">E_FAIL</span></span>|<span data-ttu-id="04a7e-123">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="04a7e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04a7e-124">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="04a7e-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04a7e-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="04a7e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04a7e-126">Notes</span><span class="sxs-lookup"><span data-stu-id="04a7e-126">Remarks</span></span>  
 <span data-ttu-id="04a7e-127">Un port de terminaison d’e/s est créé à l’aide d’un appel à `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="04a7e-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="04a7e-128">Le CLR appelle `Bind` pour lier un handle à ce port.</span><span class="sxs-lookup"><span data-stu-id="04a7e-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04a7e-129">Lorsqu’une demande d’e/s se termine, l’hôte doit appeler la [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="04a7e-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a7e-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="04a7e-130">Requirements</span></span>  
 <span data-ttu-id="04a7e-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a7e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a7e-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="04a7e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04a7e-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04a7e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04a7e-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a7e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a7e-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04a7e-135">See Also</span></span>  
 [<span data-ttu-id="04a7e-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="04a7e-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
