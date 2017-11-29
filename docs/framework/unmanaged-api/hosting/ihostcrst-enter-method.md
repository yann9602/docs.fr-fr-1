---
title: "IHostCrst::Enter, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.Enter
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d209e13360616295f166ad23c65b0c4e764af79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="a4808-102">IHostCrst::Enter, méthode</span><span class="sxs-lookup"><span data-stu-id="a4808-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="a4808-103">Accède à la section critique qui est représentée par les [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="a4808-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4808-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4808-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4808-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4808-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="a4808-106">[in] Parmi les [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeurs indiquant quelle action l’hôte doit effectuer si l’opération se bloque.</span><span class="sxs-lookup"><span data-stu-id="a4808-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4808-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a4808-107">Return Value</span></span>  
  
|<span data-ttu-id="a4808-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4808-108">HRESULT</span></span>|<span data-ttu-id="a4808-109">Description</span><span class="sxs-lookup"><span data-stu-id="a4808-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4808-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4808-110">S_OK</span></span>|<span data-ttu-id="a4808-111">`Enter`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a4808-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="a4808-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a4808-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a4808-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="a4808-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a4808-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a4808-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a4808-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a4808-115">The call timed out.</span></span>|  
|<span data-ttu-id="a4808-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a4808-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a4808-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a4808-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a4808-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a4808-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a4808-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="a4808-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a4808-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4808-120">E_FAIL</span></span>|<span data-ttu-id="a4808-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a4808-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a4808-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a4808-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a4808-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a4808-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4808-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="a4808-124">Remarks</span></span>  
 <span data-ttu-id="a4808-125">`Enter`reflète Win32 `EnterCriticalSection` (fonction).</span><span class="sxs-lookup"><span data-stu-id="a4808-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4808-126">Cette méthode ne retourne pas tant que l’entrée de la section critique.</span><span class="sxs-lookup"><span data-stu-id="a4808-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4808-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a4808-127">Requirements</span></span>  
 <span data-ttu-id="a4808-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4808-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4808-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4808-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4808-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4808-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4808-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4808-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4808-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4808-132">See Also</span></span>  
 [<span data-ttu-id="a4808-133">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="a4808-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="a4808-134">IHostCrst (Interface)</span><span class="sxs-lookup"><span data-stu-id="a4808-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="a4808-135">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="a4808-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
