---
title: "ICLRAppDomainResourceMonitor::GetCurrentAllocated, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dee616e1fbd071662a42af856fa2cd51f7bdd5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="a74e5-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated, méthode</span><span class="sxs-lookup"><span data-stu-id="a74e5-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="a74e5-103">Obtient la taille totale, en octets, de toutes les allocations de mémoire effectuées par le domaine d’application depuis sa création, sans soustraire la mémoire qui a été par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="a74e5-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a74e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a74e5-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a74e5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a74e5-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="a74e5-106">[in] L’ID du domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="a74e5-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="a74e5-107">[out] Pointeur vers la taille totale de toutes les allocations de mémoire.</span><span class="sxs-lookup"><span data-stu-id="a74e5-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a74e5-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a74e5-108">Return Value</span></span>  
 <span data-ttu-id="a74e5-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a74e5-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a74e5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a74e5-110">HRESULT</span></span>|<span data-ttu-id="a74e5-111">Description</span><span class="sxs-lookup"><span data-stu-id="a74e5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a74e5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a74e5-112">S_OK</span></span>|<span data-ttu-id="a74e5-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="a74e5-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="a74e5-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="a74e5-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="a74e5-115">Le domaine d’application a été déchargé ou n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="a74e5-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a74e5-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="a74e5-116">Remarks</span></span>  
 <span data-ttu-id="a74e5-117">Cette méthode est l’équivalent non managé de managé <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="a74e5-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a74e5-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a74e5-118">Requirements</span></span>  
 <span data-ttu-id="a74e5-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a74e5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a74e5-120">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a74e5-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a74e5-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a74e5-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a74e5-122">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a74e5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74e5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a74e5-123">See Also</span></span>  
 [<span data-ttu-id="a74e5-124">ICLRAppDomainResourceMonitor (Interface)</span><span class="sxs-lookup"><span data-stu-id="a74e5-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="a74e5-125">Analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="a74e5-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="a74e5-126">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="a74e5-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a74e5-127">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="a74e5-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
