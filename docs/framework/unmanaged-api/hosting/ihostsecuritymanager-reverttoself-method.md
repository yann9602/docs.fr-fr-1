---
title: "IHostSecurityManager::RevertToSelf, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.RevertToSelf
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0fad325bc3df54f412a797e9944f5b1f38615786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="d50da-102">IHostSecurityManager::RevertToSelf, méthode</span><span class="sxs-lookup"><span data-stu-id="d50da-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="d50da-103">Met fin à l’emprunt d’identité de l’utilisateur actuel et retourne le jeton de thread d’origine.</span><span class="sxs-lookup"><span data-stu-id="d50da-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d50da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d50da-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d50da-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d50da-105">Return Value</span></span>  
  
|<span data-ttu-id="d50da-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d50da-106">HRESULT</span></span>|<span data-ttu-id="d50da-107">Description</span><span class="sxs-lookup"><span data-stu-id="d50da-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d50da-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d50da-108">S_OK</span></span>|<span data-ttu-id="d50da-109">`RevertToSelf`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d50da-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="d50da-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d50da-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d50da-111">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="d50da-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d50da-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d50da-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d50da-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d50da-113">The call timed out.</span></span>|  
|<span data-ttu-id="d50da-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d50da-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d50da-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d50da-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d50da-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d50da-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d50da-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="d50da-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d50da-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d50da-118">E_FAIL</span></span>|<span data-ttu-id="d50da-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d50da-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d50da-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d50da-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d50da-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d50da-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d50da-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="d50da-122">Remarks</span></span>  
 <span data-ttu-id="d50da-123">`RevertToSelf`est appelée pour retourner au jeton de thread d’origine, après un appel antérieur à la [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d50da-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d50da-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d50da-124">Requirements</span></span>  
 <span data-ttu-id="d50da-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d50da-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d50da-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d50da-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d50da-127">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d50da-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d50da-128">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d50da-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d50da-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d50da-129">See Also</span></span>  
 [<span data-ttu-id="d50da-130">IHostSecurityContext (Interface)</span><span class="sxs-lookup"><span data-stu-id="d50da-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="d50da-131">IHostSecurityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="d50da-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="d50da-132">ImpersonateLoggedOnUser (méthode)</span><span class="sxs-lookup"><span data-stu-id="d50da-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
