---
title: AssemblyBindInfo, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdf76b95e80d5d4d96d2b5ed8236018147167905
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="7efbd-102">AssemblyBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="7efbd-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="7efbd-103">Fournit des informations détaillées sur l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7efbd-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7efbd-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="7efbd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="7efbd-105">Members</span></span>  
  
|<span data-ttu-id="7efbd-106">Membre</span><span class="sxs-lookup"><span data-stu-id="7efbd-106">Member</span></span>|<span data-ttu-id="7efbd-107">Description</span><span class="sxs-lookup"><span data-stu-id="7efbd-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="7efbd-108">Un identificateur unique pour le `IStream` retourné par un appel à [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), à partir de laquelle l’assembly référencé doit être chargé.</span><span class="sxs-lookup"><span data-stu-id="7efbd-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="7efbd-109">Identificateur unique pour l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7efbd-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="7efbd-110">Identificateur de l’assembly référencé après l’application de toutes les valeurs de stratégie de liaison.</span><span class="sxs-lookup"><span data-stu-id="7efbd-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="7efbd-111">Parmi les [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs qui indiquent quelles stratégies de contrôle de version, le cas échéant, doivent être appliqués à l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7efbd-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7efbd-112">Notes</span><span class="sxs-lookup"><span data-stu-id="7efbd-112">Remarks</span></span>  
 <span data-ttu-id="7efbd-113">L’hôte fournit l’identificateur unique `dwAppDomainId` pour le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7efbd-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="7efbd-114">Après un appel à `IHostAssemblyStore::ProvideAssembly` retourne, le runtime utilise l’identificateur pour déterminer si le contenu de la `IStream` a été mappé.</span><span class="sxs-lookup"><span data-stu-id="7efbd-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="7efbd-115">Dans ce cas, le runtime charge la copie existante plutôt que de remapper le flux.</span><span class="sxs-lookup"><span data-stu-id="7efbd-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="7efbd-116">Le runtime utilise également cet identificateur en tant que clé de recherche des flux retournés d’appels à [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="7efbd-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="7efbd-117">Par conséquent, l’identificateur doit être unique pour les demandes du module et des requêtes de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7efbd-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7efbd-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7efbd-118">Requirements</span></span>  
 <span data-ttu-id="7efbd-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7efbd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7efbd-120">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="7efbd-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7efbd-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7efbd-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7efbd-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7efbd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efbd-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7efbd-123">See Also</span></span>  
 [<span data-ttu-id="7efbd-124">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="7efbd-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="7efbd-125">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="7efbd-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="7efbd-126">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="7efbd-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="7efbd-127">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="7efbd-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="7efbd-128">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="7efbd-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="7efbd-129">ModuleBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="7efbd-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
