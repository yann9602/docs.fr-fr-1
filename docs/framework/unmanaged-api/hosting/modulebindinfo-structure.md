---
title: ModuleBindInfo, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6488503e0300530b22c0c6f904e11db7f5d5b41c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="f1739-102">ModuleBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="f1739-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="f1739-103">Fournit des informations détaillées sur le module référencé et de l’assembly qui le contient.</span><span class="sxs-lookup"><span data-stu-id="f1739-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1739-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1739-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="f1739-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f1739-105">Members</span></span>  
  
|<span data-ttu-id="f1739-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f1739-106">Member</span></span>|<span data-ttu-id="f1739-107">Description</span><span class="sxs-lookup"><span data-stu-id="f1739-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="f1739-108">Un identificateur unique pour le `IStream` qui est retourné par un appel à la [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) méthode à partir de laquelle le module référencé doit être chargé.</span><span class="sxs-lookup"><span data-stu-id="f1739-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="f1739-109">Identificateur unique de l’assembly qui contient le module référencé.</span><span class="sxs-lookup"><span data-stu-id="f1739-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="f1739-110">Le nom du module référencé.</span><span class="sxs-lookup"><span data-stu-id="f1739-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1739-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f1739-111">Remarks</span></span>  
 <span data-ttu-id="f1739-112">`ModuleBindInfo`est passé en tant que paramètre à `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="f1739-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="f1739-113">L’hôte fournit l’identificateur unique `dwAppDomainId` pour le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f1739-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="f1739-114">Après un appel à la [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) méthode est retournée, le runtime utilise l’identificateur pour déterminer si le contenu de la `IStream` a été mappé.</span><span class="sxs-lookup"><span data-stu-id="f1739-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="f1739-115">Dans ce cas, le runtime charge la copie existante plutôt que de remapper le flux.</span><span class="sxs-lookup"><span data-stu-id="f1739-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="f1739-116">Le runtime utilise également cet identificateur en tant que clé de recherche pour les flux qui sont retournées à partir des appels à la `IHostAssemblyStore::ProvideAssembly` (méthode).</span><span class="sxs-lookup"><span data-stu-id="f1739-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="f1739-117">Par conséquent, l’identificateur doit être unique pour les demandes de module ainsi que pour les demandes d’assembly.</span><span class="sxs-lookup"><span data-stu-id="f1739-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1739-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f1739-118">Requirements</span></span>  
 <span data-ttu-id="f1739-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1739-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1739-120">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="f1739-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f1739-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1739-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1739-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1739-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1739-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1739-123">See Also</span></span>  
 [<span data-ttu-id="f1739-124">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f1739-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="f1739-125">AssemblyBindInfo (Structure)</span><span class="sxs-lookup"><span data-stu-id="f1739-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [<span data-ttu-id="f1739-126">ICLRAssemblyIdentityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="f1739-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="f1739-127">ICLRAssemblyReferenceList (Interface)</span><span class="sxs-lookup"><span data-stu-id="f1739-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="f1739-128">IHostAssemblyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="f1739-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
