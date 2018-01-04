---
title: "ICLRHostProtectionManager::SetProtectedCategories, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetProtectedCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0971e93f02420966d6561c5b7d4dce8b75e222fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="8fa58-102">ICLRHostProtectionManager::SetProtectedCategories, méthode</span><span class="sxs-lookup"><span data-stu-id="8fa58-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="8fa58-103">Spécifie les catégories de types managés et les membres ne doivent pas recevoir de s’exécuter dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="8fa58-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fa58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fa58-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fa58-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8fa58-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="8fa58-106">[in] Une combinaison de [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) valeurs indiquant les catégories de types managés et les membres ne doivent pas recevoir de s’exécuter dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="8fa58-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fa58-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8fa58-107">Return Value</span></span>  
  
|<span data-ttu-id="8fa58-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8fa58-108">HRESULT</span></span>|<span data-ttu-id="8fa58-109">Description</span><span class="sxs-lookup"><span data-stu-id="8fa58-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8fa58-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8fa58-110">S_OK</span></span>|<span data-ttu-id="8fa58-111">`SetProtectedCategories`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8fa58-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="8fa58-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8fa58-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8fa58-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="8fa58-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8fa58-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8fa58-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8fa58-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8fa58-115">The call timed out.</span></span>|  
|<span data-ttu-id="8fa58-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8fa58-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8fa58-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8fa58-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8fa58-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8fa58-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8fa58-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="8fa58-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8fa58-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8fa58-120">E_FAIL</span></span>|<span data-ttu-id="8fa58-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8fa58-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8fa58-122">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8fa58-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8fa58-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8fa58-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fa58-124">Notes</span><span class="sxs-lookup"><span data-stu-id="8fa58-124">Remarks</span></span>  
 <span data-ttu-id="8fa58-125">Chaque `EApiCategories` valeur fait référence à une liste de types et membres managés.</span><span class="sxs-lookup"><span data-stu-id="8fa58-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="8fa58-126">Le `EApiCategories` énumération et la `SetProtectedCategories` méthode sont directement liés à la <xref:System.Security.Permissions.HostProtectionAttribute> (classe), qui est utilisé pour marquer des types managés et les membres qui exposent des fonctions correspondant aux catégories décrites par `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="8fa58-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="8fa58-127">Pour plus d’informations, consultez <xref:System.Security.Permissions.HostProtectionAttribute> et <xref:System.Security.Permissions.HostProtectionResource> énumération, qui correspond directement au `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="8fa58-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fa58-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8fa58-128">Requirements</span></span>  
 <span data-ttu-id="8fa58-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fa58-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fa58-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8fa58-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8fa58-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fa58-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8fa58-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fa58-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fa58-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fa58-133">See Also</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>  
 [<span data-ttu-id="8fa58-134">EApiCategories, énumération</span><span class="sxs-lookup"><span data-stu-id="8fa58-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="8fa58-135">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="8fa58-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="8fa58-136">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="8fa58-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
