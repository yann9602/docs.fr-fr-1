---
title: IHostSecurityContext, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityContext
helpviewer_keywords: IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1d3c616ced761b696f50e9207e6fad312f06c31c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="13c5e-102">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="13c5e-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="13c5e-103">Permet le common language runtime (CLR) pour gérer les informations de contexte de sécurité implémentées par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="13c5e-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13c5e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="13c5e-104">Methods</span></span>  
  
|<span data-ttu-id="13c5e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="13c5e-105">Method</span></span>|<span data-ttu-id="13c5e-106">Description</span><span class="sxs-lookup"><span data-stu-id="13c5e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13c5e-107">Capture, méthode</span><span class="sxs-lookup"><span data-stu-id="13c5e-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="13c5e-108">Obtient un clone de le `IHostSecurityContext` instance retournée à partir d’un appel à [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="13c5e-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13c5e-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="13c5e-109">Remarks</span></span>  
 <span data-ttu-id="13c5e-110">Un hôte peut contrôler tous les accès du code aux jetons de threads par le CLR et l’utilisateur du code.</span><span class="sxs-lookup"><span data-stu-id="13c5e-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="13c5e-111">Il peut également garantir que la sécurité complète les informations de contexte sont passées aux opérations asynchrones ou des points de code avec accès restreint au code.</span><span class="sxs-lookup"><span data-stu-id="13c5e-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="13c5e-112">`IHostSecurityContext`encapsule ces informations de contexte de sécurité, qui sont opaques pour le runtime.</span><span class="sxs-lookup"><span data-stu-id="13c5e-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="13c5e-113">Le runtime intercepte cette information à l’aide de `Capture`, et les déplace dans la répartition d’élément de travail de pool de threads, l’exécution du finaliseur et les constructeurs de module et de classe.</span><span class="sxs-lookup"><span data-stu-id="13c5e-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c5e-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="13c5e-114">Requirements</span></span>  
 <span data-ttu-id="13c5e-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c5e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c5e-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13c5e-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13c5e-117">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13c5e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13c5e-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c5e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c5e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13c5e-119">See Also</span></span>  
 [<span data-ttu-id="13c5e-120">ICLRHostProtectionManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="13c5e-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="13c5e-121">IHostSecurityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="13c5e-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="13c5e-122">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="13c5e-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
