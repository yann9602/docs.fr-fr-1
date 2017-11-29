---
title: ICLRPolicyManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager
helpviewer_keywords: ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3dd904184b730a5b0f5b2dfcac4197e708544d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="93e6f-102">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="93e6f-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="93e6f-103">Fournit des méthodes qui permettent à l’hôte spécifier les actions à entreprendre en cas de défaillances et des délais d’expiration de stratégie.</span><span class="sxs-lookup"><span data-stu-id="93e6f-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93e6f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="93e6f-104">Methods</span></span>  
  
|<span data-ttu-id="93e6f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="93e6f-105">Method</span></span>|<span data-ttu-id="93e6f-106">Description</span><span class="sxs-lookup"><span data-stu-id="93e6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93e6f-107">SetActionOnFailure (méthode)</span><span class="sxs-lookup"><span data-stu-id="93e6f-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="93e6f-108">Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre en cas d’échec spécifié.</span><span class="sxs-lookup"><span data-stu-id="93e6f-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="93e6f-109">SetActionOnTimeout (méthode)</span><span class="sxs-lookup"><span data-stu-id="93e6f-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="93e6f-110">Spécifie l’action de stratégie que le CLR doit entreprendre lorsque l’opération spécifiée arrive à expiration.</span><span class="sxs-lookup"><span data-stu-id="93e6f-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="93e6f-111">SetDefaultAction (méthode)</span><span class="sxs-lookup"><span data-stu-id="93e6f-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="93e6f-112">Spécifie l’action de stratégie que le CLR doit entreprendre lorsque l’opération spécifiée se produit.</span><span class="sxs-lookup"><span data-stu-id="93e6f-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="93e6f-113">SetTimeout (méthode)</span><span class="sxs-lookup"><span data-stu-id="93e6f-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="93e6f-114">Définit une valeur de délai d’attente pour l’opération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="93e6f-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="93e6f-115">SetTimeoutAndAction (méthode)</span><span class="sxs-lookup"><span data-stu-id="93e6f-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="93e6f-116">Définit une valeur de délai d’attente pour l’opération spécifiée et spécifie l’action de stratégie que le CLR doit entreprendre lorsque l’opération se produit.</span><span class="sxs-lookup"><span data-stu-id="93e6f-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="93e6f-117">SetUnhandledExceptionPolicy (méthode)</span><span class="sxs-lookup"><span data-stu-id="93e6f-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="93e6f-118">Spécifie le comportement du CLR lorsqu’une exception non gérée se produit.</span><span class="sxs-lookup"><span data-stu-id="93e6f-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93e6f-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="93e6f-119">Requirements</span></span>  
 <span data-ttu-id="93e6f-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93e6f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93e6f-121">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93e6f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93e6f-122">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93e6f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93e6f-123">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93e6f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e6f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93e6f-124">See Also</span></span>  
 [<span data-ttu-id="93e6f-125">EClrFailure (énumération)</span><span class="sxs-lookup"><span data-stu-id="93e6f-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="93e6f-126">EClrOperation (énumération)</span><span class="sxs-lookup"><span data-stu-id="93e6f-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="93e6f-127">EPolicyAction (énumération)</span><span class="sxs-lookup"><span data-stu-id="93e6f-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="93e6f-128">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="93e6f-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
