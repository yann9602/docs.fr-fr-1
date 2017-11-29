---
title: ICLRAssemblyIdentityManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager
helpviewer_keywords: ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d7fe632941c4cf0c20841ece390d2f41f28337d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="468df-102">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="468df-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="468df-103">Fournit des méthodes qui prennent en charge la communication entre l’hôte et le common language runtime (CLR) sur les assemblys.</span><span class="sxs-lookup"><span data-stu-id="468df-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="468df-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="468df-104">Methods</span></span>  
  
|<span data-ttu-id="468df-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="468df-105">Method</span></span>|<span data-ttu-id="468df-106">Description</span><span class="sxs-lookup"><span data-stu-id="468df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="468df-107">GetBindingIdentityFromFile (méthode)</span><span class="sxs-lookup"><span data-stu-id="468df-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="468df-108">Obtient l’identité d’assembly une liaison de données pour l’assembly sur le chemin d’accès de fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="468df-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="468df-109">GetBindingIdentityFromStream (méthode)</span><span class="sxs-lookup"><span data-stu-id="468df-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="468df-110">Obtient les données d’identité canonique de l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="468df-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="468df-111">GetCLRAssemblyReferenceList (méthode)</span><span class="sxs-lookup"><span data-stu-id="468df-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="468df-112">Obtient un [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance à partir de la liste fournie d’identités d’assembly partielles.</span><span class="sxs-lookup"><span data-stu-id="468df-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="468df-113">GetProbingAssembliesFromReference (méthode)</span><span class="sxs-lookup"><span data-stu-id="468df-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="468df-114">Obtient un [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) énumérateur pour les identités d’assembly référencé par l’assembly ayant l’identité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="468df-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="468df-115">GetReferencedAssembliesFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="468df-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="468df-116">Obtient un [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance qui contient une liste des assemblys référencés par l’assembly dans le chemin d’accès de fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="468df-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="468df-117">GetReferencedAssembliesFromStream (méthode)</span><span class="sxs-lookup"><span data-stu-id="468df-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="468df-118">Obtient un pointeur vers un `ICLRReferenceAssemblyEnum` objet qui contient les données d’identité pour les assemblys référencés par l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="468df-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="468df-119">IsStronglyNamed (méthode)</span><span class="sxs-lookup"><span data-stu-id="468df-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="468df-120">Obtient une valeur qui indique si l’assembly spécifié est un nom fort.</span><span class="sxs-lookup"><span data-stu-id="468df-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="468df-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="468df-121">Remarks</span></span>  
 <span data-ttu-id="468df-122">Utilisez `ICLRAssemblyIdentityManager` pour obtenir des instances de `ICLRAssemblyReferenceList` et énumérer des identités d’assembly.</span><span class="sxs-lookup"><span data-stu-id="468df-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="468df-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="468df-123">Requirements</span></span>  
 <span data-ttu-id="468df-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="468df-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="468df-125">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="468df-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="468df-126">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="468df-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="468df-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="468df-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="468df-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="468df-128">See Also</span></span>  
 [<span data-ttu-id="468df-129">ICLRAssemblyReferenceList (Interface)</span><span class="sxs-lookup"><span data-stu-id="468df-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="468df-130">ICLRProbingAssemblyEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="468df-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="468df-131">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="468df-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
