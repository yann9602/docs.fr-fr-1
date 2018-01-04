---
title: IHostControl, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostControl
helpviewer_keywords: IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d0eaecef4cc34549c7d37953a5c8144bdd983692
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="9eed8-102">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="9eed8-102">IHostControl Interface</span></span>
<span data-ttu-id="9eed8-103">Fournit des méthodes pour configurer le chargement d’assemblys et pour déterminer quelles interfaces d’hébergement l’hôte prend en charge.</span><span class="sxs-lookup"><span data-stu-id="9eed8-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9eed8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9eed8-104">Methods</span></span>  
  
|<span data-ttu-id="9eed8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9eed8-105">Method</span></span>|<span data-ttu-id="9eed8-106">Description</span><span class="sxs-lookup"><span data-stu-id="9eed8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9eed8-107">GetHostManager, méthode</span><span class="sxs-lookup"><span data-stu-id="9eed8-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="9eed8-108">Obtient un pointeur d’interface à l’implémentation de l’hôte de l’interface avec l’objet `IID`.</span><span class="sxs-lookup"><span data-stu-id="9eed8-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="9eed8-109">SetAppDomainManager, méthode</span><span class="sxs-lookup"><span data-stu-id="9eed8-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="9eed8-110">Avertit l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="9eed8-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9eed8-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9eed8-111">Requirements</span></span>  
 <span data-ttu-id="9eed8-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eed8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eed8-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9eed8-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9eed8-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9eed8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9eed8-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eed8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eed8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eed8-116">See Also</span></span>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="9eed8-117">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="9eed8-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="9eed8-118">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="9eed8-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="9eed8-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9eed8-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
