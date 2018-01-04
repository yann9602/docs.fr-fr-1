---
title: IHostPolicyManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager
helpviewer_keywords: IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0efbc0c51121156d112c63ba4ae59c6c9e95cd95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="5d6c3-102">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="5d6c3-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="5d6c3-103">Fournit des méthodes qui informent l’hôte des actions que le common language runtime (CLR) effectue en cas d’abandon, les délais d’attente ou d’échec.</span><span class="sxs-lookup"><span data-stu-id="5d6c3-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d6c3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5d6c3-104">Methods</span></span>  
  
|<span data-ttu-id="5d6c3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5d6c3-105">Method</span></span>|<span data-ttu-id="5d6c3-106">Description</span><span class="sxs-lookup"><span data-stu-id="5d6c3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d6c3-107">OnDefaultAction, méthode</span><span class="sxs-lookup"><span data-stu-id="5d6c3-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="5d6c3-108">Avertit l’hôte que le CLR est sur le point d’effectuer l’action par défaut spécifiée par un appel à [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) en réponse à un thread d’abandonner ou <xref:System.AppDomain> décharger.</span><span class="sxs-lookup"><span data-stu-id="5d6c3-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="5d6c3-109">OnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="5d6c3-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="5d6c3-110">Avertit l’hôte que le CLR est sur le point d’effectuer l’action spécifiée par un appel à [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) en réponse à une ressource d’allocation ou un échec.</span><span class="sxs-lookup"><span data-stu-id="5d6c3-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="5d6c3-111">OnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="5d6c3-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="5d6c3-112">Avertit l’hôte que le CLR est sur le point d’effectuer l’action spécifiée par un appel à [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) en réponse à un délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="5d6c3-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d6c3-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5d6c3-113">Requirements</span></span>  
 <span data-ttu-id="5d6c3-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d6c3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d6c3-115">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d6c3-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d6c3-116">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d6c3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d6c3-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d6c3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d6c3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d6c3-118">See Also</span></span>  
 [<span data-ttu-id="5d6c3-119">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="5d6c3-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="5d6c3-120">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="5d6c3-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="5d6c3-121">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="5d6c3-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="5d6c3-122">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="5d6c3-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="5d6c3-123">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="5d6c3-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
