---
title: IHostAssemblyManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager
helpviewer_keywords: IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 351824c1b915183a8e157f5bb2e01a414027a178
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="ebe4a-102">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="ebe4a-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="ebe4a-103">Fournit des méthodes qui permettent à un hôte spécifier des ensembles d’assemblys qui doivent être chargés par le common language runtime (CLR) ou par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="ebe4a-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebe4a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ebe4a-104">Methods</span></span>  
  
|<span data-ttu-id="ebe4a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ebe4a-105">Method</span></span>|<span data-ttu-id="ebe4a-106">Description</span><span class="sxs-lookup"><span data-stu-id="ebe4a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebe4a-107">GetAssemblyStore, méthode</span><span class="sxs-lookup"><span data-stu-id="ebe4a-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="ebe4a-108">Obtient un pointeur d’interface vers un [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) qui représente la liste des assemblys chargés par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="ebe4a-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="ebe4a-109">GetNonHostStoreAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="ebe4a-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="ebe4a-110">Obtient un pointeur d’interface vers un [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) qui représente la liste des assemblys que l’hôte attend le CLR à charger.</span><span class="sxs-lookup"><span data-stu-id="ebe4a-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebe4a-111">Notes</span><span class="sxs-lookup"><span data-stu-id="ebe4a-111">Remarks</span></span>  
 <span data-ttu-id="ebe4a-112">L’ordinateur hôte n’est pas requis pour implémenter `IHostAssemblyManager` ou `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="ebe4a-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="ebe4a-113">Si l’hôte n’implémente pas `IHostAssemblyManager`, il doit également implémenter `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="ebe4a-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="ebe4a-114">L’exécution des requêtes pour un `IHostAssemblyManager` en appelant [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) lors de l’initialisation avec un `IID` d’IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="ebe4a-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebe4a-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ebe4a-115">Requirements</span></span>  
 <span data-ttu-id="ebe4a-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebe4a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebe4a-117">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ebe4a-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebe4a-118">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebe4a-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebe4a-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebe4a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe4a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebe4a-120">See Also</span></span>  
 [<span data-ttu-id="ebe4a-121">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="ebe4a-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="ebe4a-122">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="ebe4a-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="ebe4a-123">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="ebe4a-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="ebe4a-124">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="ebe4a-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
