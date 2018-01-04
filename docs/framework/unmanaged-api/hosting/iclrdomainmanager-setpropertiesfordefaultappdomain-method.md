---
title: "ICLRDomainManager::SetPropertiesForDefaultAppDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de72568f5908dc89c9a4105c927cfba6c7366b80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="ae5d8-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="ae5d8-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="ae5d8-103">Définit les propriétés qui servira à initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="ae5d8-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae5d8-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae5d8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae5d8-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="ae5d8-106">[in] Le nombre d’entrées dans `pwszPropertyNames` et `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="ae5d8-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="ae5d8-107">[in] Un tableau de noms de propriété, ou null si aucune propriété.</span><span class="sxs-lookup"><span data-stu-id="ae5d8-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="ae5d8-108">Actuellement, le seul nom de propriété reconnu par cette méthode est « PARTIAL_TRUST_VISIBLE_ASSEMBLIES ».</span><span class="sxs-lookup"><span data-stu-id="ae5d8-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="ae5d8-109">[in] Un tableau de valeurs de propriété, ou null si aucune propriété.</span><span class="sxs-lookup"><span data-stu-id="ae5d8-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae5d8-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ae5d8-110">Return Value</span></span>  
 <span data-ttu-id="ae5d8-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ae5d8-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ae5d8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae5d8-112">HRESULT</span></span>|<span data-ttu-id="ae5d8-113">Description</span><span class="sxs-lookup"><span data-stu-id="ae5d8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae5d8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae5d8-114">S_OK</span></span>|<span data-ttu-id="ae5d8-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="ae5d8-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="ae5d8-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="ae5d8-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="ae5d8-117">`pwszPropertyNames`inclut un nom de propriété qui n’est pas reconnu par cette méthode.</span><span class="sxs-lookup"><span data-stu-id="ae5d8-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae5d8-118">Notes</span><span class="sxs-lookup"><span data-stu-id="ae5d8-118">Remarks</span></span>  
 <span data-ttu-id="ae5d8-119">La valeur de propriété pour « PARTIAL_TRUST_VISIBLE_ASSEMBLIES » est une liste d’assemblys qui ont l’attribut conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ) l’attribut APTCA (avec le <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> indicateur, qui est rendues visibles aux appelants partiellement approuvés dans l’application par défaut domaine.</span><span class="sxs-lookup"><span data-stu-id="ae5d8-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae5d8-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae5d8-120">Requirements</span></span>  
 <span data-ttu-id="ae5d8-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae5d8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae5d8-122">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ae5d8-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ae5d8-123">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae5d8-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae5d8-124">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae5d8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae5d8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae5d8-125">See Also</span></span>  
 [<span data-ttu-id="ae5d8-126">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="ae5d8-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="ae5d8-127">ICLRDomainManager, interface</span><span class="sxs-lookup"><span data-stu-id="ae5d8-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
