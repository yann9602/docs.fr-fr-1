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
ms.openlocfilehash: 7e72ad562a73faf5682204c2ae2583b71cb3c05e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="eeefb-102">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="eeefb-102">IHostControl Interface</span></span>
<span data-ttu-id="eeefb-103">Fournit des méthodes pour configurer le chargement d’assemblys et pour déterminer quelles interfaces d’hébergement l’hôte prend en charge.</span><span class="sxs-lookup"><span data-stu-id="eeefb-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eeefb-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="eeefb-104">Methods</span></span>  
  
|<span data-ttu-id="eeefb-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="eeefb-105">Method</span></span>|<span data-ttu-id="eeefb-106">Description</span><span class="sxs-lookup"><span data-stu-id="eeefb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eeefb-107">GetHostManager (méthode)</span><span class="sxs-lookup"><span data-stu-id="eeefb-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="eeefb-108">Obtient un pointeur d’interface à l’implémentation de l’hôte de l’interface avec l’objet `IID`.</span><span class="sxs-lookup"><span data-stu-id="eeefb-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="eeefb-109">SetAppDomainManager (méthode)</span><span class="sxs-lookup"><span data-stu-id="eeefb-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="eeefb-110">Avertit l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="eeefb-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eeefb-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eeefb-111">Requirements</span></span>  
 <span data-ttu-id="eeefb-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeefb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeefb-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eeefb-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eeefb-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eeefb-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eeefb-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeefb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeefb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eeefb-116">See Also</span></span>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="eeefb-117">ICLRRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="eeefb-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="eeefb-118">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="eeefb-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="eeefb-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="eeefb-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
