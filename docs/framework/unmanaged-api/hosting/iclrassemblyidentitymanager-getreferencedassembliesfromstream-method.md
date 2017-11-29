---
title: "ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64a43640d08acbab0bcf505cc8a5850784ff18ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="79ed2-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="79ed2-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="79ed2-103">Obtient un pointeur vers un [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) objet qui contient les données d’identité pour les assemblys référencés par l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="79ed2-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ed2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79ed2-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79ed2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79ed2-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="79ed2-106">[in] Pointeur d’interface vers un `IStream` contenant l’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="79ed2-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="79ed2-107">[in] Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="79ed2-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="79ed2-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur de la version actuelle du common language runtime (CLR) prend en charge.</span><span class="sxs-lookup"><span data-stu-id="79ed2-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="79ed2-109">[in] Un pointeur vers un [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objet qui contient les données d’identité pour les assemblys à exclure de `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="79ed2-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="79ed2-110">[out] Un pointeur vers l’adresse d’un `ICLRReferenceAssemblyEnum` objet qui contient les données d’identité pour les assemblys référencés par l’assembly dans `pStream`, à l’exclusion des assemblys dans `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="79ed2-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79ed2-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="79ed2-111">Return Value</span></span>  
  
|<span data-ttu-id="79ed2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79ed2-112">HRESULT</span></span>|<span data-ttu-id="79ed2-113">Description</span><span class="sxs-lookup"><span data-stu-id="79ed2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79ed2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="79ed2-114">S_OK</span></span>|<span data-ttu-id="79ed2-115">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="79ed2-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="79ed2-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79ed2-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79ed2-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="79ed2-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79ed2-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79ed2-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79ed2-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="79ed2-119">The call timed out.</span></span>|  
|<span data-ttu-id="79ed2-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79ed2-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79ed2-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="79ed2-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79ed2-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79ed2-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79ed2-123">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="79ed2-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79ed2-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79ed2-124">E_FAIL</span></span>|<span data-ttu-id="79ed2-125">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="79ed2-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79ed2-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="79ed2-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79ed2-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="79ed2-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79ed2-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="79ed2-128">Remarks</span></span>  
 <span data-ttu-id="79ed2-129">L’appelant peut choisir d’exclure un ensemble de références d’assembly connues de la liste retournée.</span><span class="sxs-lookup"><span data-stu-id="79ed2-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="79ed2-130">Ce jeu est défini par `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="79ed2-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79ed2-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="79ed2-131">Requirements</span></span>  
 <span data-ttu-id="79ed2-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79ed2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79ed2-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79ed2-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79ed2-134">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79ed2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79ed2-135">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79ed2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ed2-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79ed2-136">See Also</span></span>  
 [<span data-ttu-id="79ed2-137">ICLRAssemblyIdentityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="79ed2-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="79ed2-138">ICLRAssemblyReferenceList (Interface)</span><span class="sxs-lookup"><span data-stu-id="79ed2-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="79ed2-139">ICLRReferenceAssemblyEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="79ed2-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
