---
title: "IHostPolicyManager::OnFailure, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager.OnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd8c5e071eca6b287b570006f33d7a1a43c1def9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="25371-102">IHostPolicyManager::OnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="25371-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="25371-103">Avertit l’hôte que le common language runtime (CLR) est sur le point d’effectuer l’action spécifiée par un appel à la [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) méthode en réponse à une ressource d’allocation ou un échec.</span><span class="sxs-lookup"><span data-stu-id="25371-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25371-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25371-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25371-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25371-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="25371-106">[in] Parmi les [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valeurs indiquant le genre d’échec auquel le CLR répond.</span><span class="sxs-lookup"><span data-stu-id="25371-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="25371-107">[in] Parmi les [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs, indiquant l’action que le CLR effectue en réponse à `failure`.</span><span class="sxs-lookup"><span data-stu-id="25371-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25371-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="25371-108">Return Value</span></span>  
  
|<span data-ttu-id="25371-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25371-109">HRESULT</span></span>|<span data-ttu-id="25371-110">Description</span><span class="sxs-lookup"><span data-stu-id="25371-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25371-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="25371-111">S_OK</span></span>|<span data-ttu-id="25371-112">`OnFailure`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="25371-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="25371-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25371-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25371-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="25371-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25371-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25371-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25371-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="25371-116">The call timed out.</span></span>|  
|<span data-ttu-id="25371-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25371-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25371-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="25371-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25371-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25371-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25371-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="25371-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25371-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25371-121">E_FAIL</span></span>|<span data-ttu-id="25371-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="25371-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25371-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="25371-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25371-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="25371-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25371-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="25371-125">Requirements</span></span>  
 <span data-ttu-id="25371-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25371-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25371-127">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25371-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25371-128">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25371-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25371-129">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25371-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25371-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25371-130">See Also</span></span>  
 [<span data-ttu-id="25371-131">EClrFailure (énumération)</span><span class="sxs-lookup"><span data-stu-id="25371-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="25371-132">EPolicyAction (énumération)</span><span class="sxs-lookup"><span data-stu-id="25371-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="25371-133">ICLRPolicyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="25371-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="25371-134">IHostPolicyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="25371-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
