---
title: IGCThreadControl, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCThreadControl
helpviewer_keywords: IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66afef7dec0637e98249838ae06ae6f1161df3f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="cd81b-102">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="cd81b-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="cd81b-103">Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="cd81b-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd81b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="cd81b-104">Methods</span></span>  
  
|<span data-ttu-id="cd81b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="cd81b-105">Method</span></span>|<span data-ttu-id="cd81b-106">Description</span><span class="sxs-lookup"><span data-stu-id="cd81b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd81b-107">SuspensionEnding (méthode)</span><span class="sxs-lookup"><span data-stu-id="cd81b-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="cd81b-108">Avertit l’hôte que le runtime est la reprise de threads après un garbage collection ou une suspension.</span><span class="sxs-lookup"><span data-stu-id="cd81b-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="cd81b-109">SuspensionStarting (méthode)</span><span class="sxs-lookup"><span data-stu-id="cd81b-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="cd81b-110">Avertit l’hôte que le runtime débute une suspension du thread pour un garbage collection ou une suspension.</span><span class="sxs-lookup"><span data-stu-id="cd81b-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="cd81b-111">ThreadIsBlockingForSuspension (méthode)</span><span class="sxs-lookup"><span data-stu-id="cd81b-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="cd81b-112">Avertit l’hôte que le thread qui effectue l’appel va bloquer, peut-être pour un garbage collection ou une suspension.</span><span class="sxs-lookup"><span data-stu-id="cd81b-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd81b-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cd81b-113">Requirements</span></span>  
 <span data-ttu-id="cd81b-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd81b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd81b-115">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd81b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd81b-116">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd81b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd81b-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd81b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd81b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd81b-118">See Also</span></span>  
 [<span data-ttu-id="cd81b-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="cd81b-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
