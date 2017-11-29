---
title: ICLRMetaHostPolicy, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b8cbe1d397e1214cfa4d3f4cbc3d6cdf2d3ccd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="2c5db-102">ICLRMetaHostPolicy, interface</span><span class="sxs-lookup"><span data-stu-id="2c5db-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="2c5db-103">Fournit la [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) méthode, qui retourne un pointeur vers une interface du common language runtime (CLR) selon un critère de stratégie, managé fichier de configuration, de la version et de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="2c5db-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c5db-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2c5db-104">Methods</span></span>  
  
|<span data-ttu-id="2c5db-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2c5db-105">Method</span></span>|<span data-ttu-id="2c5db-106">Description</span><span class="sxs-lookup"><span data-stu-id="2c5db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c5db-107">GetRequestedRuntime (méthode)</span><span class="sxs-lookup"><span data-stu-id="2c5db-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="2c5db-108">Fournit une interface CLR par défaut selon un critère de stratégie, géré de fichier d’assembly, version et la configuration.</span><span class="sxs-lookup"><span data-stu-id="2c5db-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c5db-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="2c5db-109">Remarks</span></span>  
 <span data-ttu-id="2c5db-110">Vous pouvez obtenir une référence à cette interface en appelant le [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fonctionne comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2c5db-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="2c5db-111">Cette interface ne prend pas réellement charger et activer le CLR, mais retourne simplement la version CLR par défaut selon les versions disponibles qui sont installées ou chargées.</span><span class="sxs-lookup"><span data-stu-id="2c5db-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="2c5db-112">Le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] API d’hébergement consolide les stratégies de sorte que les hôtes avec des besoins spécifiques puissent utiliser les fonctionnalités de base sans encourir des pénalités imprévues.</span><span class="sxs-lookup"><span data-stu-id="2c5db-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="2c5db-113">Par exemple, la plupart des exportations MSCorEE.dll liera à un CLR spécifique, bien qu’une méthode peut logiquement impose pas.</span><span class="sxs-lookup"><span data-stu-id="2c5db-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="2c5db-114">Le [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) énumération fournit des stratégies de liaison qui sont communes à la majorité des ordinateurs hôtes.</span><span class="sxs-lookup"><span data-stu-id="2c5db-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c5db-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2c5db-115">Requirements</span></span>  
 <span data-ttu-id="2c5db-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c5db-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c5db-117">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2c5db-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2c5db-118">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c5db-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c5db-119">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c5db-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c5db-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c5db-120">See Also</span></span>  
 [<span data-ttu-id="2c5db-121">Interfaces d’hébergement CLR est ajouté dans le .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="2c5db-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="2c5db-122">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="2c5db-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="2c5db-123">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="2c5db-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
