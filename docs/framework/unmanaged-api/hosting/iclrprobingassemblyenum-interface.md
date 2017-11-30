---
title: ICLRProbingAssemblyEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum
helpviewer_keywords: ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6d810ab6e62c6df1b00305947de552ecdbe82141
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="f153a-102">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f153a-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="f153a-103">Fournit des méthodes qui permettent à l’hôte d’obtenir les identités d’identification d’un assembly à l’aide des informations d’identité de l’assembly qui est internes pour le common language runtime (CLR), sans avoir à créer ou à comprendre cette identité.</span><span class="sxs-lookup"><span data-stu-id="f153a-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f153a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f153a-104">Methods</span></span>  
  
|<span data-ttu-id="f153a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f153a-105">Method</span></span>|<span data-ttu-id="f153a-106">Description</span><span class="sxs-lookup"><span data-stu-id="f153a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f153a-107">Get (méthode)</span><span class="sxs-lookup"><span data-stu-id="f153a-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="f153a-108">Obtient l’identité d’assembly à l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="f153a-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f153a-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f153a-109">Remarks</span></span>  
 <span data-ttu-id="f153a-110">Les méthodes telles que [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) renvoyer un `ICLRProbingAssemblyEnum` instance.</span><span class="sxs-lookup"><span data-stu-id="f153a-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f153a-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f153a-111">Requirements</span></span>  
 <span data-ttu-id="f153a-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f153a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f153a-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f153a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f153a-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f153a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f153a-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f153a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f153a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f153a-116">See Also</span></span>  
 [<span data-ttu-id="f153a-117">ICLRAssemblyIdentityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="f153a-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="f153a-118">ICLRAssemblyReferenceList (Interface)</span><span class="sxs-lookup"><span data-stu-id="f153a-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="f153a-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f153a-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
