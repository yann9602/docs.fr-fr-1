---
title: "ICLRDebugManager::IsDebuggerAttached, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.IsDebuggerAttached
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 986c9ab7853324d1a2f0fc104399141068ae9a09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="8ccc2-102">ICLRDebugManager::IsDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="8ccc2-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="8ccc2-103">Obtient une valeur qui indique si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ccc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ccc2-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ccc2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ccc2-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="8ccc2-106">[out] `true` si un débogueur est attaché au processus ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ccc2-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8ccc2-107">Return Value</span></span>  
  
|<span data-ttu-id="8ccc2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ccc2-108">HRESULT</span></span>|<span data-ttu-id="8ccc2-109">Description</span><span class="sxs-lookup"><span data-stu-id="8ccc2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ccc2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ccc2-110">S_OK</span></span>|<span data-ttu-id="8ccc2-111">`IsDebuggerAttached`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="8ccc2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ccc2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ccc2-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ccc2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ccc2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ccc2-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-115">The call timed out.</span></span>|  
|<span data-ttu-id="8ccc2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ccc2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ccc2-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ccc2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ccc2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ccc2-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ccc2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ccc2-120">E_FAIL</span></span>|<span data-ttu-id="8ccc2-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ccc2-122">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ccc2-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ccc2-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ccc2-124">Remarks</span></span>  
 <span data-ttu-id="8ccc2-125">`IsDebuggerAttached`permet à l’hôte d’interroger le CLR pour déterminer si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="8ccc2-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ccc2-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ccc2-126">Requirements</span></span>  
 <span data-ttu-id="8ccc2-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ccc2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ccc2-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ccc2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ccc2-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ccc2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ccc2-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ccc2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccc2-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ccc2-131">See Also</span></span>  
 [<span data-ttu-id="8ccc2-132">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="8ccc2-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="8ccc2-133">ICLRDebugManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="8ccc2-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="8ccc2-134">IHostControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="8ccc2-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
