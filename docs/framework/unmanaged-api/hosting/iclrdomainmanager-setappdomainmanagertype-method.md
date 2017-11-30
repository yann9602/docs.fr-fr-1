---
title: "ICLRDomainManager::SetAppDomainManagerType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17c99d21155d8f985ea455e171067855edcafedc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="17344-102">ICLRDomainManager::SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="17344-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="17344-103">Spécifie le type, dérivé de la <xref:System.AppDomainManager?displayProperty=nameWithType> classe, le Gestionnaire de domaine d’application qui servira à initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="17344-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17344-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17344-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17344-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17344-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="17344-106">[in] Le nom complet de l’assembly qui contient le type de gestionnaire de domaine application ; par exemple : « AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3 ».</span><span class="sxs-lookup"><span data-stu-id="17344-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="17344-107">[in] Nom du type de gestionnaire de domaine, y compris l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="17344-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="17344-108">[in] Une combinaison de [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) valeurs d’énumération qui fournissent des informations sur le Gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="17344-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17344-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="17344-109">Return Value</span></span>  
 <span data-ttu-id="17344-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="17344-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="17344-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17344-111">HRESULT</span></span>|<span data-ttu-id="17344-112">Description</span><span class="sxs-lookup"><span data-stu-id="17344-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17344-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="17344-113">S_OK</span></span>|<span data-ttu-id="17344-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="17344-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="17344-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17344-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17344-116">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="17344-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17344-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="17344-117">Remarks</span></span>  
 <span data-ttu-id="17344-118">Actuellement, la seule valeur définie pour `dwInitializeDomainFlags` est `eInitializeNewDomainFlags_NoSecurityChanges`, qui indique le common language runtime (CLR) que le Gestionnaire de domaine d’application ne modifiera pas de paramètres de sécurité pendant l’exécution de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="17344-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="17344-119">Cela permet au CLR optimiser le chargement des assemblys qui ont l’attribut conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA).</span><span class="sxs-lookup"><span data-stu-id="17344-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="17344-120">Si la fermeture transitive de ce jeu d’assemblys est importante, cela peut entraîner une amélioration significative du temps de démarrage.</span><span class="sxs-lookup"><span data-stu-id="17344-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="17344-121">Si l’hôte spécifie `eInitializeNewDomainFlags_NoSecurityChanges` pour le Gestionnaire de domaine d’application, un <xref:System.InvalidOperationException> est levée si une tentative est faite pour modifier la sécurité du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="17344-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="17344-122">Appel de la [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)méthode équivaut à appeler la méthode `ICLRDomainManager::SetAppDomainManagerType` avec `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="17344-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17344-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="17344-123">Requirements</span></span>  
 <span data-ttu-id="17344-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17344-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17344-125">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="17344-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="17344-126">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17344-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17344-127">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17344-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17344-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17344-128">See Also</span></span>  
 [<span data-ttu-id="17344-129">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="17344-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="17344-130">ICLRDomainManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="17344-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="17344-131">EInitializeNewDomainFlags (énumération)</span><span class="sxs-lookup"><span data-stu-id="17344-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
