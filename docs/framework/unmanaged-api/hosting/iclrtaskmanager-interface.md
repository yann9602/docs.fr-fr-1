---
title: ICLRTaskManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager
helpviewer_keywords: ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 342d7b82802fcfbe9e179d85d6d692205f19e382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="036ec-102">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="036ec-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="036ec-103">Fournit des méthodes qui permettent à l’hôte à demander explicitement que le common language runtime (CLR) créent une nouvelle tâche, obtenir la tâche en cours d’exécution et définir le langage géographique et la culture pour la tâche.</span><span class="sxs-lookup"><span data-stu-id="036ec-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="036ec-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="036ec-104">Methods</span></span>  
  
|<span data-ttu-id="036ec-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="036ec-105">Method</span></span>|<span data-ttu-id="036ec-106">Description</span><span class="sxs-lookup"><span data-stu-id="036ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="036ec-107">CreateTask, méthode</span><span class="sxs-lookup"><span data-stu-id="036ec-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="036ec-108">Demande explicitement que le CLR crée une nouvelle [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="036ec-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="036ec-109">GetCurrentTask, méthode</span><span class="sxs-lookup"><span data-stu-id="036ec-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="036ec-110">Obtient le `ICLRTask` instance qui représente la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="036ec-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="036ec-111">GetCurrentTaskType, méthode</span><span class="sxs-lookup"><span data-stu-id="036ec-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="036ec-112">Obtient le type de la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="036ec-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="036ec-113">SetLocale, méthode</span><span class="sxs-lookup"><span data-stu-id="036ec-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="036ec-114">Notifie le CLR que l’hôte a modifié l’identificateur de paramètres régionaux sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="036ec-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="036ec-115">SetUILocale, méthode</span><span class="sxs-lookup"><span data-stu-id="036ec-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="036ec-116">Notifie le common language runtime que l’hôte a modifié l’identificateur de paramètres régionaux d’interface utilisateur de la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="036ec-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="036ec-117">Notes</span><span class="sxs-lookup"><span data-stu-id="036ec-117">Remarks</span></span>  
 <span data-ttu-id="036ec-118">Chaque tâche qui s’exécute dans un environnement hébergé a des représentations à la fois côté hôte (une instance de [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) et sur le côté CLR (une instance de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="036ec-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="036ec-119">L’hôte ou le CLR peut lancer la création d’une tâche, mais la représentation côté hôte doit être associée à une représentation côté CLR correspondante pour garantir une bonne communication entre l’hôte et le CLR concernant la tâche.</span><span class="sxs-lookup"><span data-stu-id="036ec-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="036ec-120">Les deux objets doivent être créés et instanciés avant que le code managé peut s’exécuter sur un thread de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="036ec-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="036ec-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="036ec-121">Requirements</span></span>  
 <span data-ttu-id="036ec-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="036ec-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="036ec-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="036ec-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="036ec-124">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="036ec-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="036ec-125">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="036ec-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036ec-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="036ec-126">See Also</span></span>  
 [<span data-ttu-id="036ec-127">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="036ec-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="036ec-128">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="036ec-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="036ec-129">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="036ec-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="036ec-130">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="036ec-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
