---
title: IHostAssemblyStore, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c795d4baa3030817299f23c3dadf4caf7a5edc5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="a911d-102">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="a911d-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="a911d-103">Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a911d-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a911d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a911d-104">Methods</span></span>  
  
|<span data-ttu-id="a911d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="a911d-105">Method</span></span>|<span data-ttu-id="a911d-106">Description</span><span class="sxs-lookup"><span data-stu-id="a911d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a911d-107">ProvideAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="a911d-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="a911d-108">Obtient une référence à un assembly qui n’est pas référencé par le [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retourné par un appel à [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="a911d-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="a911d-109">ProvideModule, méthode</span><span class="sxs-lookup"><span data-stu-id="a911d-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="a911d-110">Résout un module dans un assembly ou un fichier de ressources (non incorporé) lié.</span><span class="sxs-lookup"><span data-stu-id="a911d-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a911d-111">Notes</span><span class="sxs-lookup"><span data-stu-id="a911d-111">Remarks</span></span>  
 <span data-ttu-id="a911d-112">`IHostAssemblyStore`fournit un moyen pour un hôte de charger efficacement des assemblys selon identité d’assembly.</span><span class="sxs-lookup"><span data-stu-id="a911d-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="a911d-113">L’hôte charge les assemblys en retournant `IStream` instances qui pointent directement vers les octets.</span><span class="sxs-lookup"><span data-stu-id="a911d-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="a911d-114">Le CLR détermine si un hôte a implémenté `IHostAssemblyStore` en appelant `IHostAssemblyManager::GetNonHostAssemblyStores` lors de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="a911d-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="a911d-115">Cela permet à l’hôte, par exemple, de contrôler la liaison aux assemblys d’utilisateur, mais s’appuyer sur le runtime pour la liaison aux assemblys .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a911d-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a911d-116">Fournir une implémentation de `IHostAssemblyStore`, l’hôte spécifie son intention de résoudre tous les assemblys qui ne sont pas référencés par le `ICLRAssemblyReferenceList` retourné par `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="a911d-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a911d-117">La version 2.0 du .NET Framework ne fournit pas un moyen de l’hôte de charger l’image native d’un assembly, tel que fourni par le [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utilitaire.</span><span class="sxs-lookup"><span data-stu-id="a911d-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a911d-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a911d-118">Requirements</span></span>  
 <span data-ttu-id="a911d-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a911d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a911d-120">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a911d-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a911d-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a911d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a911d-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a911d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a911d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a911d-123">See Also</span></span>  
 [<span data-ttu-id="a911d-124">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="a911d-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="a911d-125">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="a911d-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="a911d-126">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="a911d-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
