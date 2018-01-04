---
title: ICLRDebugManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e712f22156e96cfc58e9c1a835077ba21ecd184
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="aeb52-102">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="aeb52-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="aeb52-103">Fournit des méthodes qui permettent à un hôte à associer un ensemble de tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="aeb52-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aeb52-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="aeb52-104">Methods</span></span>  
  
|<span data-ttu-id="aeb52-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="aeb52-105">Method</span></span>|<span data-ttu-id="aeb52-106">Description</span><span class="sxs-lookup"><span data-stu-id="aeb52-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aeb52-107">BeginConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="aeb52-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="aeb52-108">Établit une connexion entre l’hôte et le débogueur pour associer des tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="aeb52-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="aeb52-109">EndConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="aeb52-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="aeb52-110">Supprime l’association entre une liste de tâches et un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="aeb52-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="aeb52-111">GetDacl, méthode</span><span class="sxs-lookup"><span data-stu-id="aeb52-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="aeb52-112">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="aeb52-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="aeb52-113">IsDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="aeb52-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="aeb52-114">Obtient une valeur qui indique si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="aeb52-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="aeb52-115">SetConnectionTasks, méthode</span><span class="sxs-lookup"><span data-stu-id="aeb52-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="aeb52-116">Associe une liste de [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances avec un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="aeb52-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="aeb52-117">SetDacl, méthode</span><span class="sxs-lookup"><span data-stu-id="aeb52-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="aeb52-118">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="aeb52-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="aeb52-119">SetSymbolReadingPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="aeb52-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="aeb52-120">Définit la stratégie pour la lecture des fichiers de programme (PDB) de la base de données.</span><span class="sxs-lookup"><span data-stu-id="aeb52-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="aeb52-121">La stratégie détermine si les informations sur les fichiers et les numéros de ligne sont incluses dans les piles d’appels.</span><span class="sxs-lookup"><span data-stu-id="aeb52-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeb52-122">Notes</span><span class="sxs-lookup"><span data-stu-id="aeb52-122">Remarks</span></span>  
 <span data-ttu-id="aeb52-123">Dans les scénarios de débogage, un hôte peut souhaiter regrouper des tâches en fonction de sa propre logique de programmation.</span><span class="sxs-lookup"><span data-stu-id="aeb52-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="aeb52-124">Par exemple, un regroupement permettrait à un développeur d’afficher uniquement les tâches requises par les API du développeur, au lieu d’afficher toutes les tâches en cours d’exécution dans le processus.</span><span class="sxs-lookup"><span data-stu-id="aeb52-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="aeb52-125">`ICLRDebugManager`permet à l’hôte implémenter ce type de regroupement.</span><span class="sxs-lookup"><span data-stu-id="aeb52-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aeb52-126">Trois `ICLRDebugManager` méthodes, `BeginConnection`, `SetConnectionTasks` et `EndConnection`, dépendent les uns des autres.</span><span class="sxs-lookup"><span data-stu-id="aeb52-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="aeb52-127">Elles doivent être appelées dans l’ordre indiqué à fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="aeb52-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="aeb52-128">Le regroupement et les identificateurs et les noms conviviaux que l’hôte assigne au regroupement, n’ont aucune signification pour le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="aeb52-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="aeb52-129">Le CLR passe simplement les informations au débogueur.</span><span class="sxs-lookup"><span data-stu-id="aeb52-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb52-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aeb52-130">Requirements</span></span>  
 <span data-ttu-id="aeb52-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeb52-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb52-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aeb52-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeb52-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aeb52-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeb52-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb52-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb52-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aeb52-135">See Also</span></span>  
 [<span data-ttu-id="aeb52-136">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="aeb52-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
