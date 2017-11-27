---
title: "IHostControl::SetAppDomainManager, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostControl.SetAppDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97e853bc74babca5b5400953b63714a13419fcaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="f6b2c-102">IHostControl::SetAppDomainManager, méthode</span><span class="sxs-lookup"><span data-stu-id="f6b2c-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="f6b2c-103">Avertit l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6b2c-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6b2c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6b2c-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="f6b2c-106">[in] L’identificateur numérique du <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="f6b2c-107">[in] Un pointeur vers le <xref:System.AppDomainManager> objet que l’hôte implémente en tant que `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6b2c-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f6b2c-108">Return Value</span></span>  
  
|<span data-ttu-id="f6b2c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6b2c-109">HRESULT</span></span>|<span data-ttu-id="f6b2c-110">Description</span><span class="sxs-lookup"><span data-stu-id="f6b2c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6b2c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6b2c-111">S_OK</span></span>|<span data-ttu-id="f6b2c-112">`SetAppDomainManager`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="f6b2c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6b2c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6b2c-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6b2c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6b2c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6b2c-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-116">The call timed out.</span></span>|  
|<span data-ttu-id="f6b2c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6b2c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6b2c-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6b2c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6b2c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6b2c-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6b2c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6b2c-121">E_FAIL</span></span>|<span data-ttu-id="f6b2c-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6b2c-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f6b2c-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6b2c-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6b2c-125">Remarks</span></span>  
 <span data-ttu-id="f6b2c-126">Le <xref:System.AppDomainManager> fournit à l’hôte avec un mécanisme d’amorçage dans du code managé et de contrôler la création et les paramètres de chaque <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="f6b2c-127">Le <xref:System.AppDomainManager> est chargé dans chaque <xref:System.AppDomain> lorsque qui <xref:System.AppDomain> est créé.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="f6b2c-128">Si elle choisit, le CLR informe l’hôte que le domaine d’application a été créé en définissant la valeur de le `pUnkAppDomainManager` paramètre.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="f6b2c-129">Dans son implémentation de la `SetAppDomainManager` (méthode), l’hôte peut définir le nom de l’assembly et le type pour le Gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="f6b2c-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6b2c-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f6b2c-130">Requirements</span></span>  
 <span data-ttu-id="f6b2c-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6b2c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6b2c-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6b2c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6b2c-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6b2c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6b2c-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6b2c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b2c-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6b2c-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="f6b2c-136">IHostControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="f6b2c-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
