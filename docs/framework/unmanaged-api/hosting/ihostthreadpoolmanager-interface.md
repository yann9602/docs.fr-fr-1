---
title: IHostThreadPoolManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager
helpviewer_keywords: IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1cd58c53deec0a895ae6f67cccf26d2c8c2530be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="2cf5f-102">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="2cf5f-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="2cf5f-103">Fournit des méthodes qui permettent le common language runtime (CLR) pour configurer le pool de threads et en file d’attente des éléments de travail au pool de threads.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cf5f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2cf5f-104">Methods</span></span>  
  
|<span data-ttu-id="2cf5f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2cf5f-105">Method</span></span>|<span data-ttu-id="2cf5f-106">Description</span><span class="sxs-lookup"><span data-stu-id="2cf5f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cf5f-107">GetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="2cf5f-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="2cf5f-108">Obtient le nombre de threads du pool de threads qui ne traitent pas actuellement des éléments de travail.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="2cf5f-109">GetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="2cf5f-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="2cf5f-110">Obtient le nombre maximal de threads que l’hôte conserve simultanément dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="2cf5f-111">GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="2cf5f-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="2cf5f-112">Obtient le nombre minimal de threads inactifs que l’hôte gère en anticipation des demandes.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="2cf5f-113">QueueUserWorkItem, méthode</span><span class="sxs-lookup"><span data-stu-id="2cf5f-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="2cf5f-114">Une fonction pour l’exécution des files d’attente et fournit un objet contenant les données à utiliser par la fonction.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="2cf5f-115">SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="2cf5f-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="2cf5f-116">Définit le nombre maximal de threads que l’hôte peut gérer dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="2cf5f-117">SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="2cf5f-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="2cf5f-118">Définit le nombre minimal de threads inactifs que l’hôte doit gérer en anticipation des demandes.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cf5f-119">Notes</span><span class="sxs-lookup"><span data-stu-id="2cf5f-119">Remarks</span></span>  
 <span data-ttu-id="2cf5f-120">L’ordinateur hôte n’est pas requis pour configurer le pool de threads à l’aide des valeurs spécifiées dans les appels à la `SetMaxThreads` et `SetMinThreads` méthodes.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="2cf5f-121">Dans ce cas, l’hôte doit retourner une valeur HRESULT d’E_NOTIMPL à partir de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="2cf5f-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf5f-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2cf5f-122">Requirements</span></span>  
 <span data-ttu-id="2cf5f-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cf5f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cf5f-124">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2cf5f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cf5f-125">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2cf5f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cf5f-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cf5f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf5f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cf5f-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="2cf5f-128">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="2cf5f-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
