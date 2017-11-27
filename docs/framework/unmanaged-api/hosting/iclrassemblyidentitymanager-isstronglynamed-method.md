---
title: "ICLRAssemblyIdentityManager::IsStronglyNamed, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.IsStronglyNamed
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d0cb0bcaf5d19ec088511e64baffff9031911b32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="05d02-102">ICLRAssemblyIdentityManager::IsStronglyNamed, méthode</span><span class="sxs-lookup"><span data-stu-id="05d02-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="05d02-103">Obtient une valeur qui indique si l’assembly spécifié est un nom fort.</span><span class="sxs-lookup"><span data-stu-id="05d02-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05d02-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05d02-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05d02-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="05d02-106">[in] Les données d’identité assembly canonique opaque de l’assembly à évaluer.</span><span class="sxs-lookup"><span data-stu-id="05d02-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="05d02-107">[out] `true`, si l’assembly référencé par le `pwzAssemblyIdentity` paramètre est fortement nommés ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="05d02-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05d02-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="05d02-108">Return Value</span></span>  
  
|<span data-ttu-id="05d02-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05d02-109">HRESULT</span></span>|<span data-ttu-id="05d02-110">Description</span><span class="sxs-lookup"><span data-stu-id="05d02-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05d02-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="05d02-111">S_OK</span></span>|<span data-ttu-id="05d02-112">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="05d02-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="05d02-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05d02-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05d02-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="05d02-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05d02-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05d02-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05d02-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="05d02-116">The call timed out.</span></span>|  
|<span data-ttu-id="05d02-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05d02-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05d02-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="05d02-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05d02-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05d02-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05d02-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="05d02-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05d02-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05d02-121">E_FAIL</span></span>|<span data-ttu-id="05d02-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="05d02-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05d02-123">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="05d02-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05d02-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="05d02-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05d02-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="05d02-125">Requirements</span></span>  
 <span data-ttu-id="05d02-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05d02-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d02-127">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05d02-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05d02-128">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05d02-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05d02-129">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d02-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d02-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05d02-130">See Also</span></span>  
 [<span data-ttu-id="05d02-131">ICLRAssemblyIdentityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="05d02-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
