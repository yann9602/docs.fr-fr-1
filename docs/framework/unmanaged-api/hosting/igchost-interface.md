---
title: IGCHost, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost
helpviewer_keywords: IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0f398c09569a855291a1565ce63b513161a803
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="igchost-interface"></a><span data-ttu-id="e99ec-102">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="e99ec-102">IGCHost Interface</span></span>
<span data-ttu-id="e99ec-103">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et contrôler certains aspects du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e99ec-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e99ec-104">En commençant par le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], vous pouvez utiliser la [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment de garbage collection et la taille maximale de la génération du système de garbage collection 0 pour les valeurs supérieure à la `DWORD` limite imposée par le [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="e99ec-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e99ec-105">Cette interface est uniquement à l’usage expert.</span><span class="sxs-lookup"><span data-stu-id="e99ec-105">This interface is for expert usage only.</span></span> <span data-ttu-id="e99ec-106">Il peut affecter les performances d’une application pour une utilisation incorrecte.</span><span class="sxs-lookup"><span data-stu-id="e99ec-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e99ec-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e99ec-107">Methods</span></span>  
  
|<span data-ttu-id="e99ec-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="e99ec-108">Method</span></span>|<span data-ttu-id="e99ec-109">Description</span><span class="sxs-lookup"><span data-stu-id="e99ec-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e99ec-110">Collect (méthode)</span><span class="sxs-lookup"><span data-stu-id="e99ec-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="e99ec-111">Force une collection pour la génération donnée, quel que soit l’état du garbage collection en cours.</span><span class="sxs-lookup"><span data-stu-id="e99ec-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="e99ec-112">GetStats (méthode)</span><span class="sxs-lookup"><span data-stu-id="e99ec-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="e99ec-113">Obtient les statistiques de l’état actuel du système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e99ec-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="e99ec-114">GetThreadStats (méthode)</span><span class="sxs-lookup"><span data-stu-id="e99ec-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="e99ec-115">Obtient les statistiques par thread pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e99ec-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="e99ec-116">SetGCStartupLimits (méthode)</span><span class="sxs-lookup"><span data-stu-id="e99ec-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="e99ec-117">Définit la taille du segment et la taille maximale pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="e99ec-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="e99ec-118">SetVirtualMemLimit (méthode)</span><span class="sxs-lookup"><span data-stu-id="e99ec-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="e99ec-119">Définit la taille maximale de mémoire virtuelle du runtime.</span><span class="sxs-lookup"><span data-stu-id="e99ec-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e99ec-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e99ec-120">Requirements</span></span>  
 <span data-ttu-id="e99ec-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e99ec-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e99ec-122">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="e99ec-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e99ec-123">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e99ec-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e99ec-124">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e99ec-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e99ec-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e99ec-125">See Also</span></span>  
 [<span data-ttu-id="e99ec-126">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="e99ec-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="e99ec-127">Corruntimehost, coclasse</span><span class="sxs-lookup"><span data-stu-id="e99ec-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
