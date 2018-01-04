---
title: "ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f255db046f4c7d698ad864723167e81952481519
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="fb97a-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference, méthode</span><span class="sxs-lookup"><span data-stu-id="fb97a-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="fb97a-103">Obtient un [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) énumérateur pour les identités d’assembly référencé par l’assembly avec le type de l’identité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fb97a-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb97a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb97a-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb97a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fb97a-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="fb97a-106">[in] Une valeur valide qui spécifie l’architecture de processeur, tel que défini dans WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="fb97a-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fb97a-107">[in] Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="fb97a-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="fb97a-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur de la version actuelle du common language runtime (CLR) prend en charge.</span><span class="sxs-lookup"><span data-stu-id="fb97a-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="fb97a-109">[in] Une identité de liaison d’assembly opaque, généralement retournée à partir d’un appel à la [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) ou [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="fb97a-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="fb97a-110">[out] Pointeur d’interface vers un `ICLRProbingAssemblyEnum` énumérateur qui contient des références aux assemblys référencés par l’assembly identifié par `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="fb97a-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb97a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fb97a-111">Return Value</span></span>  
  
|<span data-ttu-id="fb97a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb97a-112">HRESULT</span></span>|<span data-ttu-id="fb97a-113">Description</span><span class="sxs-lookup"><span data-stu-id="fb97a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb97a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb97a-114">S_OK</span></span>|<span data-ttu-id="fb97a-115">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="fb97a-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="fb97a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb97a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb97a-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="fb97a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb97a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb97a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb97a-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="fb97a-119">The call timed out.</span></span>|  
|<span data-ttu-id="fb97a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb97a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb97a-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="fb97a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb97a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb97a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb97a-123">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="fb97a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb97a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb97a-124">E_FAIL</span></span>|<span data-ttu-id="fb97a-125">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fb97a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb97a-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fb97a-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb97a-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fb97a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb97a-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fb97a-128">Requirements</span></span>  
 <span data-ttu-id="fb97a-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb97a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb97a-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb97a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb97a-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb97a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb97a-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb97a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb97a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb97a-133">See Also</span></span>  
 [<span data-ttu-id="fb97a-134">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="fb97a-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="fb97a-135">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="fb97a-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="fb97a-136">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="fb97a-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
