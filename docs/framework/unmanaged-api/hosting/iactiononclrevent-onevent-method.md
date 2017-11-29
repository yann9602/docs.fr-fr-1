---
title: "IActionOnCLREvent::OnEvent, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent.OnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b2f609969ccf67f07701d20578225f1618293968
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="fe125-102">IActionOnCLREvent::OnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="fe125-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="fe125-103">Exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="fe125-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe125-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe125-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe125-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe125-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="fe125-106">[in] Parmi les [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) valeurs, qui indique le type d’événement.</span><span class="sxs-lookup"><span data-stu-id="fe125-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="fe125-107">[in] Un pointeur vers un objet qui contient des détails sur `event`.</span><span class="sxs-lookup"><span data-stu-id="fe125-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe125-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fe125-108">Return Value</span></span>  
  
|<span data-ttu-id="fe125-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe125-109">HRESULT</span></span>|<span data-ttu-id="fe125-110">Description</span><span class="sxs-lookup"><span data-stu-id="fe125-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe125-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe125-111">S_OK</span></span>|<span data-ttu-id="fe125-112">`OnEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="fe125-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="fe125-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe125-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe125-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="fe125-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe125-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe125-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe125-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="fe125-116">The call timed out.</span></span>|  
|<span data-ttu-id="fe125-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe125-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe125-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="fe125-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe125-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe125-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe125-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="fe125-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe125-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe125-121">E_FAIL</span></span>|<span data-ttu-id="fe125-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fe125-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe125-123">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fe125-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe125-124">Les appels suivants à toute méthode d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fe125-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe125-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="fe125-125">Remarks</span></span>  
 <span data-ttu-id="fe125-126">Le `data` paramètre est un pointeur vers un objet de type non spécifié.</span><span class="sxs-lookup"><span data-stu-id="fe125-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="fe125-127">Si le `event` paramètre est `Event_DomainUnload`, `data` est l’identificateur numérique pour le <xref:System.AppDomain> qui a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="fe125-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="fe125-128">L’hôte peut prendre les mesures appropriées à l’aide de cet identificateur en tant que clé.</span><span class="sxs-lookup"><span data-stu-id="fe125-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="fe125-129">Si `event` est `Event_MDAFired`, `data` est un pointeur vers un [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance qui contient la sortie de message d’un Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="fe125-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="fe125-130">Assistant Débogage managé est une fonctionnalité du CLR qui aide les développeurs lors du débogage, en générant des messages XML sur les événements qui sont difficiles à intercepter.</span><span class="sxs-lookup"><span data-stu-id="fe125-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="fe125-131">Ces messages peuvent être particulièrement utiles pour déboguer des transitions entre code managé et non managé.</span><span class="sxs-lookup"><span data-stu-id="fe125-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="fe125-132">Pour plus d’informations, consultez [diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="fe125-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe125-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fe125-133">Requirements</span></span>  
 <span data-ttu-id="fe125-134">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe125-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe125-135">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe125-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe125-136">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe125-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe125-137">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe125-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe125-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe125-138">See Also</span></span>  
 [<span data-ttu-id="fe125-139">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="fe125-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="fe125-140">EClrEvent (énumération)</span><span class="sxs-lookup"><span data-stu-id="fe125-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="fe125-141">IActionOnCLREvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="fe125-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="fe125-142">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="fe125-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="fe125-143">ICLROnEventManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="fe125-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="fe125-144">MDAInfo (Structure)</span><span class="sxs-lookup"><span data-stu-id="fe125-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
