---
title: ICLRHostBindingPolicyManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager
helpviewer_keywords: ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2dd55268e9f54554ec3e9a9b61573b708aa5acc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="d51a6-102">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="d51a6-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="d51a6-103">Fournit des méthodes pour l’hôte évaluer la stratégie de liaison actuelle et de communiquer des modifications de stratégie pour un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="d51a6-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d51a6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d51a6-104">Methods</span></span>  
  
|<span data-ttu-id="d51a6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d51a6-105">Method</span></span>|<span data-ttu-id="d51a6-106">Description</span><span class="sxs-lookup"><span data-stu-id="d51a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d51a6-107">EvaluatePolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="d51a6-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="d51a6-108">Évalue la stratégie de liaison pour le compte de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="d51a6-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="d51a6-109">ModifyApplicationPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="d51a6-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="d51a6-110">Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="d51a6-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d51a6-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d51a6-111">Requirements</span></span>  
 <span data-ttu-id="d51a6-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d51a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d51a6-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d51a6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d51a6-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d51a6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d51a6-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d51a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51a6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d51a6-116">See Also</span></span>  
 [<span data-ttu-id="d51a6-117">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="d51a6-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="d51a6-118">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="d51a6-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="d51a6-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="d51a6-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
