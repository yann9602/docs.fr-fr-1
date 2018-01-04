---
title: "ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 856843cf1c4c5f1dffe23b04cf2655dfe37e476e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="6f11a-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="6f11a-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="6f11a-103">Obtient un [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance qui contient une liste des assemblys référencés par l’assembly dans le chemin d’accès de fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="6f11a-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f11a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f11a-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f11a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6f11a-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="6f11a-106">[in] Le chemin d’accès à l’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="6f11a-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6f11a-107">[in] Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="6f11a-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="6f11a-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur de la version actuelle du common language runtime (CLR) prend en charge.</span><span class="sxs-lookup"><span data-stu-id="6f11a-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="6f11a-109">[in] Un pointeur vers un [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objet qui représente les assemblys qui doivent être exclus `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="6f11a-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="6f11a-110">[out] Un pointeur vers l’adresse d’un `ICLRReferenceAssemblyEnum` objet qui contient les données d’identité pour les assemblys référencés par l’assembly dans `pwzFilePath`, à l’exclusion des assemblys représentés par `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="6f11a-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f11a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6f11a-111">Return Value</span></span>  
  
|<span data-ttu-id="6f11a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f11a-112">HRESULT</span></span>|<span data-ttu-id="6f11a-113">Description</span><span class="sxs-lookup"><span data-stu-id="6f11a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f11a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f11a-114">S_OK</span></span>|<span data-ttu-id="6f11a-115">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6f11a-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="6f11a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f11a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f11a-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="6f11a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f11a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f11a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f11a-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6f11a-119">The call timed out.</span></span>|  
|<span data-ttu-id="6f11a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f11a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f11a-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6f11a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f11a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f11a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f11a-123">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="6f11a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f11a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f11a-124">E_FAIL</span></span>|<span data-ttu-id="6f11a-125">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6f11a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f11a-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6f11a-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f11a-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6f11a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f11a-128">Notes</span><span class="sxs-lookup"><span data-stu-id="6f11a-128">Remarks</span></span>  
 <span data-ttu-id="6f11a-129">L’appelant peut choisir d’exclure un ensemble de références d’assembly connues de la liste retournée.</span><span class="sxs-lookup"><span data-stu-id="6f11a-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="6f11a-130">Ce jeu est défini par le `pExcludeAssembliesList` paramètre.</span><span class="sxs-lookup"><span data-stu-id="6f11a-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f11a-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6f11a-131">Requirements</span></span>  
 <span data-ttu-id="6f11a-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f11a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f11a-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f11a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f11a-134">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f11a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f11a-135">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f11a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f11a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f11a-136">See Also</span></span>  
 [<span data-ttu-id="6f11a-137">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="6f11a-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="6f11a-138">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="6f11a-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="6f11a-139">ICLRReferenceAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="6f11a-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
