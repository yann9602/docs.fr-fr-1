---
title: "ICLRAppDomainResourceMonitor::GetCurrentCpuTime, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2781cfb1e23db02ab8192c78bd0a3e585ee28b2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="cc872-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime, méthode</span><span class="sxs-lookup"><span data-stu-id="cc872-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="cc872-103">Obtient le temps processeur total utilisé par tous les threads pendant leur exécution dans le domaine d’application actuel, depuis le domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="cc872-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc872-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc872-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc872-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc872-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="cc872-106">[in] L’ID du domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="cc872-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="cc872-107">[out] Pointeur vers le temps processeur total utilisé par tous les threads pendant leur exécution dans le domaine d’application actuel, car le domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="cc872-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="cc872-108">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="cc872-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc872-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cc872-109">Return Value</span></span>  
  
|<span data-ttu-id="cc872-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc872-110">HRESULT</span></span>|<span data-ttu-id="cc872-111">Description</span><span class="sxs-lookup"><span data-stu-id="cc872-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc872-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc872-112">S_OK</span></span>|<span data-ttu-id="cc872-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="cc872-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="cc872-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="cc872-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="cc872-115">Le domaine d’application a été déchargé ou n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="cc872-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="cc872-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc872-116">E_FAIL</span></span>|<span data-ttu-id="cc872-117">L’analyse de ressource de domaine d’application n’est pas activé.</span><span class="sxs-lookup"><span data-stu-id="cc872-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="cc872-118">- ou -</span><span class="sxs-lookup"><span data-stu-id="cc872-118">-or-</span></span><br /><br /> <span data-ttu-id="cc872-119">Tous les autres échecs.</span><span class="sxs-lookup"><span data-stu-id="cc872-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc872-120">Notes</span><span class="sxs-lookup"><span data-stu-id="cc872-120">Remarks</span></span>  
 <span data-ttu-id="cc872-121">Cette méthode est l’équivalent non managé de managé <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="cc872-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc872-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cc872-122">Requirements</span></span>  
 <span data-ttu-id="cc872-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc872-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc872-124">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cc872-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cc872-125">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc872-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc872-126">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc872-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc872-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc872-127">See Also</span></span>  
 [<span data-ttu-id="cc872-128">ICLRAppDomainResourceMonitor, interface</span><span class="sxs-lookup"><span data-stu-id="cc872-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="cc872-129">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="cc872-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="cc872-130">Analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="cc872-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="cc872-131">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="cc872-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
