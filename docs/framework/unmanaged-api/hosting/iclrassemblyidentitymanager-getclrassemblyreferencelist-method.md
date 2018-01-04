---
title: "ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eefe5ff68c7bd428c18729dcbd792b4c3cb64c2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="ada47-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList, méthode</span><span class="sxs-lookup"><span data-stu-id="ada47-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="ada47-103">Obtient un pointeur d’interface vers un [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance à partir de la liste fournie d’identités d’assembly partielles.</span><span class="sxs-lookup"><span data-stu-id="ada47-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ada47-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ada47-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ada47-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="ada47-106">[in] Un tableau de chaînes sous la forme « nom, la propriété = valeur... » qui spécifie une liste d’identités d’assembly partielles.</span><span class="sxs-lookup"><span data-stu-id="ada47-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="ada47-107">[in] Le nombre d’éléments dans `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="ada47-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="ada47-108">[out] Pointeur d’interface vers un `ICLRAssemblyReferenceList` objet qui contient les données d’identité pour la liste des assemblys spécifiés dans `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="ada47-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ada47-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ada47-109">Return Value</span></span>  
  
|<span data-ttu-id="ada47-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ada47-110">HRESULT</span></span>|<span data-ttu-id="ada47-111">Description</span><span class="sxs-lookup"><span data-stu-id="ada47-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ada47-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ada47-112">S_OK</span></span>|<span data-ttu-id="ada47-113">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ada47-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="ada47-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ada47-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ada47-115">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="ada47-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ada47-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ada47-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ada47-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ada47-117">The call timed out.</span></span>|  
|<span data-ttu-id="ada47-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ada47-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ada47-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ada47-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ada47-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ada47-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ada47-121">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="ada47-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ada47-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ada47-122">E_FAIL</span></span>|<span data-ttu-id="ada47-123">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ada47-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ada47-124">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ada47-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ada47-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ada47-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ada47-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ada47-126">Requirements</span></span>  
 <span data-ttu-id="ada47-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada47-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada47-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ada47-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ada47-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ada47-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ada47-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada47-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada47-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ada47-131">See Also</span></span>  
 [<span data-ttu-id="ada47-132">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="ada47-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ada47-133">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="ada47-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
