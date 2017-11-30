---
title: "ICLRHostProtectionManager::SetEagerSerializeGrantSets, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a9b1e314f7af6edf3d8db00780105dff95868a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="8bb88-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets, méthode</span><span class="sxs-lookup"><span data-stu-id="8bb88-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="8bb88-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="8bb88-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bb88-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8bb88-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8bb88-105">Return Value</span></span>  
  
|<span data-ttu-id="8bb88-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8bb88-106">HRESULT</span></span>|<span data-ttu-id="8bb88-107">Description</span><span class="sxs-lookup"><span data-stu-id="8bb88-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8bb88-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8bb88-108">S_OK</span></span>|<span data-ttu-id="8bb88-109">`SetEagerSerializeGrantSets`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8bb88-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="8bb88-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8bb88-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8bb88-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="8bb88-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8bb88-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8bb88-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8bb88-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8bb88-113">The call timed out.</span></span>|  
|<span data-ttu-id="8bb88-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8bb88-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8bb88-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8bb88-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8bb88-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8bb88-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8bb88-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="8bb88-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8bb88-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8bb88-118">E_FAIL</span></span>|<span data-ttu-id="8bb88-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8bb88-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8bb88-120">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8bb88-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8bb88-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8bb88-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bb88-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8bb88-122">Requirements</span></span>  
 <span data-ttu-id="8bb88-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bb88-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bb88-124">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8bb88-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8bb88-125">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8bb88-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bb88-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bb88-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb88-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bb88-127">See Also</span></span>  
 [<span data-ttu-id="8bb88-128">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="8bb88-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="8bb88-129">ICLRHostProtectionManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="8bb88-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
