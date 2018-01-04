---
title: ICLRTask2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2
helpviewer_keywords: ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8701cff3400e46660fac90486cf5648d29aa9972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="28956-102">ICLRTask2, interface</span><span class="sxs-lookup"><span data-stu-id="28956-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="28956-103">Fournit toutes les fonctionnalités de la [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface ; en outre, fournit des méthodes qui permettent d’abandons de threads pour être retardée sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="28956-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28956-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="28956-104">Methods</span></span>  
  
|<span data-ttu-id="28956-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="28956-105">Method</span></span>|<span data-ttu-id="28956-106">Description</span><span class="sxs-lookup"><span data-stu-id="28956-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28956-107">BeginPreventAsyncAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="28956-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="28956-108">Nouveau thread de retards interrompre les requêtes sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="28956-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="28956-109">EndPreventAsyncAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="28956-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="28956-110">Permet de nouveau ou en attente de demandes d’abandon de thread de thread abandonne sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="28956-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28956-111">Notes</span><span class="sxs-lookup"><span data-stu-id="28956-111">Remarks</span></span>  
 <span data-ttu-id="28956-112">Le `ICLRTask2` interface hérite de la `ICLRTask` de l’interface et ajoute des méthodes qui permettent à l’hôte de différer les abandons de thread, pour protéger une région de code qui ne doit pas échouer.</span><span class="sxs-lookup"><span data-stu-id="28956-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="28956-113">Appel de `BeginPreventAsyncAbort` incrémente le compteur de délai d’abandon de thread pour le thread actuel et l’appel `EndPreventAsyncAbort` décrémente il.</span><span class="sxs-lookup"><span data-stu-id="28956-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="28956-114">Les appels à `BeginPreventAsyncAbort` et `EndPreventAsyncAbort` peuvent être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="28956-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="28956-115">Tant que le compteur est supérieur à zéro, pour le thread actuel abandons de thread.</span><span class="sxs-lookup"><span data-stu-id="28956-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="28956-116">Si les appels à `BeginPreventAsyncAbort` et `EndPreventAsyncAbort` sont ne pas associés, il est possible d’atteindre un état dans le thread abandons ne peut pas être remis au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="28956-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="28956-117">Le délai d’attente d’un thread qui abandonne lui-même n’est pas reconnue.</span><span class="sxs-lookup"><span data-stu-id="28956-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="28956-118">La fonctionnalité exposée par cette fonctionnalité est utilisée en interne par la machine virtuelle (VM).</span><span class="sxs-lookup"><span data-stu-id="28956-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="28956-119">Utilisation incorrecte de ces méthodes peut entraîner un comportement non spécifié dans la machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="28956-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="28956-120">Par exemple, l’appel `EndPreventAsyncAbort` sans appeler d’abord `BeginPreventAsyncAbort` Impossible de définir le compteur à zéro lorsque la machine virtuelle a précédemment incrémenté.</span><span class="sxs-lookup"><span data-stu-id="28956-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="28956-121">De même, le compteur interne n’est pas vérifié pour le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="28956-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="28956-122">Si elle dépasse sa limite intégrale, car il est incrémenté par l’hôte et la machine virtuelle, le comportement résultant n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="28956-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="28956-123">Pour plus d’informations sur les membres hérités de `ICLRTask` et sur les autres utilisations de cette interface, consultez la [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="28956-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28956-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="28956-124">Requirements</span></span>  
 <span data-ttu-id="28956-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28956-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28956-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28956-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28956-127">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28956-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28956-128">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28956-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28956-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28956-129">See Also</span></span>  
 [<span data-ttu-id="28956-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="28956-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="28956-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="28956-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="28956-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="28956-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="28956-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="28956-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="28956-134">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="28956-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
