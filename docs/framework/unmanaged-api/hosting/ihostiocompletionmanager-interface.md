---
title: IHostIoCompletionManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager
helpviewer_keywords: IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbb4b87b57d4f5e11a9dab04d20dfb73170bb4a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanager-interface"></a><span data-ttu-id="b64a3-102">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="b64a3-102">IHostIoCompletionManager Interface</span></span>
<span data-ttu-id="b64a3-103">Fournit des méthodes qui permettent le common language runtime (CLR) pour interagir avec les ports de terminaison d’e/s fournis par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="b64a3-103">Provides methods that allow the common language runtime (CLR) to interact with I/O completion ports provided by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b64a3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b64a3-104">Methods</span></span>  
  
|<span data-ttu-id="b64a3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-105">Method</span></span>|<span data-ttu-id="b64a3-106">Description</span><span class="sxs-lookup"><span data-stu-id="b64a3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b64a3-107">Bind, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-107">Bind Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|<span data-ttu-id="b64a3-108">Lie un handle à un port de terminaison d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-108">Binds a handle to an I/O completion port.</span></span>|  
|[<span data-ttu-id="b64a3-109">CloseIoCompletionPort, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-109">CloseIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|<span data-ttu-id="b64a3-110">Ferme un port qui a été créé via un appel précédent à `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="b64a3-110">Closes a port that was created through an earlier call to `CreateIoCompletionPort`.</span></span>|  
|[<span data-ttu-id="b64a3-111">CreateIoCompletionPort, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-111">CreateIoCompletionPort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|<span data-ttu-id="b64a3-112">Demande que l’hôte crée un nouveau port de terminaison d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-112">Requests that the host create a new I/O completion port.</span></span>|  
|[<span data-ttu-id="b64a3-113">GetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-113">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|<span data-ttu-id="b64a3-114">Obtient le nombre de threads de terminaison d’e/s qui ne traitent pas actuellement des demandes.</span><span class="sxs-lookup"><span data-stu-id="b64a3-114">Gets the number of I/O completion threads that are not currently processing requests.</span></span>|  
|[<span data-ttu-id="b64a3-115">GetHostOverlappedSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-115">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|<span data-ttu-id="b64a3-116">Obtient la taille des données personnalisées que l’hôte projette d’ajouter aux demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-116">Gets the size of any custom data the host intends to append to I/O requests.</span></span>|  
|[<span data-ttu-id="b64a3-117">GetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-117">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|<span data-ttu-id="b64a3-118">Obtient le nombre maximal de threads que l’hôte peut allouer pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-118">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>|  
|[<span data-ttu-id="b64a3-119">GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-119">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|<span data-ttu-id="b64a3-120">Obtient le nombre minimal de threads que l’hôte fournit pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-120">Gets the minimum number of threads that the host provides to service I/O requests.</span></span>|  
|[<span data-ttu-id="b64a3-121">InitializeHostOverlapped, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-121">InitializeHostOverlapped Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|<span data-ttu-id="b64a3-122">Fournit à l’hôte avec la possibilité d’initialiser des données personnalisées relatives à une demande d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-122">Provides the host with an opportunity to initialize any custom data about an I/O request.</span></span>|  
|[<span data-ttu-id="b64a3-123">SetCLRIoCompletionManager, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-123">SetCLRIoCompletionManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|<span data-ttu-id="b64a3-124">Fournit à l’hôte avec un pointeur d’interface vers un [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implémentée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="b64a3-124">Provides the host with an interface pointer to an [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="b64a3-125">SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-125">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|<span data-ttu-id="b64a3-126">Définit le nombre maximal de threads plus travail alloue de l’ordinateur hôte pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-126">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>|  
|[<span data-ttu-id="b64a3-127">SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="b64a3-127">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|<span data-ttu-id="b64a3-128">Définit le nombre minimal de threads que l’hôte doit allouer pour l’achèvement d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-128">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b64a3-129">Notes</span><span class="sxs-lookup"><span data-stu-id="b64a3-129">Remarks</span></span>  
 <span data-ttu-id="b64a3-130">`IHostIoCompletionManager`correspond à la `ICLRIoCompletionManager` interface implémentée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="b64a3-130">`IHostIoCompletionManager` corresponds to the `ICLRIoCompletionManager` interface implemented by the CLR.</span></span> <span data-ttu-id="b64a3-131">Le CLR appelle les méthodes de `IHostIoCompletionManager` pour lier des handles pour les ports qui fournit de l’ordinateur hôte et l’hôte appelle les méthodes de `ICLRIoCompletionManager` pour signaler la fin des demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="b64a3-131">The CLR calls the methods of `IHostIoCompletionManager` to bind handles to the ports that the host provides, and the host calls the methods of `ICLRIoCompletionManager` to report the completion of I/O requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b64a3-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b64a3-132">Requirements</span></span>  
 <span data-ttu-id="b64a3-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b64a3-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b64a3-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b64a3-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b64a3-135">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b64a3-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b64a3-136">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b64a3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64a3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b64a3-137">See Also</span></span>  
 [<span data-ttu-id="b64a3-138">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="b64a3-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
