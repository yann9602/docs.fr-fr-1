---
title: IHostCrst, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst
helpviewer_keywords: IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59485d7a642ba8b3233d5d077062e89fb2ac9b14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="93399-102">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="93399-102">IHostCrst Interface</span></span>
<span data-ttu-id="93399-103">Sert de représentation sous forme de l’hôte d’une section critique pour les threads.</span><span class="sxs-lookup"><span data-stu-id="93399-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93399-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="93399-104">Methods</span></span>  
  
|<span data-ttu-id="93399-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="93399-105">Method</span></span>|<span data-ttu-id="93399-106">Description</span><span class="sxs-lookup"><span data-stu-id="93399-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93399-107">Enter, méthode</span><span class="sxs-lookup"><span data-stu-id="93399-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="93399-108">Passe à la section critique.</span><span class="sxs-lookup"><span data-stu-id="93399-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="93399-109">Leave, méthode</span><span class="sxs-lookup"><span data-stu-id="93399-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="93399-110">Quitte la section critique.</span><span class="sxs-lookup"><span data-stu-id="93399-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="93399-111">SetSpinCount (méthode)</span><span class="sxs-lookup"><span data-stu-id="93399-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="93399-112">Définit le nombre de sélection numérique pour la section critique.</span><span class="sxs-lookup"><span data-stu-id="93399-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="93399-113">TryEnter (méthode)</span><span class="sxs-lookup"><span data-stu-id="93399-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="93399-114">Tente d’entrer immédiatement de la section critique et signale la réussite ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="93399-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93399-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="93399-115">Remarks</span></span>  
 <span data-ttu-id="93399-116">`IHostCrst`permet le common language runtime (CLR) de communiquer directement avec la représentation sous forme de l’hôte d’une section critique, au lieu d’utiliser les fonctions Win32 comme `EnterCriticalSection` ou `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="93399-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93399-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="93399-117">Requirements</span></span>  
 <span data-ttu-id="93399-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93399-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93399-119">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93399-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93399-120">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93399-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93399-121">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93399-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93399-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93399-122">See Also</span></span>  
 [<span data-ttu-id="93399-123">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="93399-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="93399-124">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="93399-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="93399-125">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="93399-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
