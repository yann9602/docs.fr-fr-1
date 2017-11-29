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
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="02b48-102">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="02b48-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="02b48-103">Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="02b48-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02b48-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="02b48-104">Methods</span></span>  
  
|<span data-ttu-id="02b48-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="02b48-105">Method</span></span>|<span data-ttu-id="02b48-106">Description</span><span class="sxs-lookup"><span data-stu-id="02b48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02b48-107">ProvideAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="02b48-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="02b48-108">Obtient une référence à un assembly qui n’est pas référencé par le [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retourné par un appel à [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="02b48-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="02b48-109">ProvideModule (méthode)</span><span class="sxs-lookup"><span data-stu-id="02b48-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="02b48-110">Résout un module dans un assembly ou un fichier de ressources (non incorporé) lié.</span><span class="sxs-lookup"><span data-stu-id="02b48-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02b48-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="02b48-111">Remarks</span></span>  
 <span data-ttu-id="02b48-112">`IHostAssemblyStore`fournit un moyen pour un hôte de charger efficacement des assemblys selon identité d’assembly.</span><span class="sxs-lookup"><span data-stu-id="02b48-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="02b48-113">L’hôte charge les assemblys en retournant `IStream` instances qui pointent directement vers les octets.</span><span class="sxs-lookup"><span data-stu-id="02b48-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="02b48-114">Le CLR détermine si un hôte a implémenté `IHostAssemblyStore` en appelant `IHostAssemblyManager::GetNonHostAssemblyStores` lors de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="02b48-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="02b48-115">Cela permet à l’hôte, par exemple, de contrôler la liaison aux assemblys d’utilisateur, mais s’appuyer sur le runtime pour la liaison aux assemblys .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02b48-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02b48-116">Fournir une implémentation de `IHostAssemblyStore`, l’hôte spécifie son intention de résoudre tous les assemblys qui ne sont pas référencés par le `ICLRAssemblyReferenceList` retourné par `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="02b48-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02b48-117">La version 2.0 du .NET Framework ne fournit pas un moyen de l’hôte de charger l’image native d’un assembly, tel que fourni par le [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utilitaire.</span><span class="sxs-lookup"><span data-stu-id="02b48-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02b48-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="02b48-118">Requirements</span></span>  
 <span data-ttu-id="02b48-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02b48-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02b48-120">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02b48-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02b48-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02b48-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02b48-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02b48-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b48-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02b48-123">See Also</span></span>  
 [<span data-ttu-id="02b48-124">ICLRAssemblyReferenceList (Interface)</span><span class="sxs-lookup"><span data-stu-id="02b48-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="02b48-125">IHostAssemblyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="02b48-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="02b48-126">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="02b48-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
