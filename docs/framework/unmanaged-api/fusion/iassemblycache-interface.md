---
title: IAssemblyCache, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21ebc29a6c442625f7a532f7b1e6a47e7dc4cb69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="6dfdd-102">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="6dfdd-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="6dfdd-103">Représente le global assembly cache pour une utilisation par la technologie de fusion.</span><span class="sxs-lookup"><span data-stu-id="6dfdd-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6dfdd-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6dfdd-104">Methods</span></span>  
  
|<span data-ttu-id="6dfdd-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="6dfdd-105">Method</span></span>|<span data-ttu-id="6dfdd-106">Description</span><span class="sxs-lookup"><span data-stu-id="6dfdd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6dfdd-107">CreateAssemblyCacheItem, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfdd-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="6dfdd-108">Obtient une référence à un nouveau [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6dfdd-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="6dfdd-109">CreateAssemblyScavenger, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfdd-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="6dfdd-110">Réservé à un usage interne par la technologie de fusion.</span><span class="sxs-lookup"><span data-stu-id="6dfdd-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="6dfdd-111">InstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfdd-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="6dfdd-112">Installe l’assembly spécifié dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="6dfdd-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="6dfdd-113">QueryAssemblyInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfdd-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="6dfdd-114">Obtient les données demandées sur l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="6dfdd-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="6dfdd-115">UninstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfdd-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="6dfdd-116">Désinstalle l’assembly spécifié du global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="6dfdd-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6dfdd-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6dfdd-117">Requirements</span></span>  
 <span data-ttu-id="6dfdd-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dfdd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dfdd-119">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6dfdd-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6dfdd-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dfdd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfdd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dfdd-121">See Also</span></span>  
 [<span data-ttu-id="6dfdd-122">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="6dfdd-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="6dfdd-123">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="6dfdd-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
