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
ms.openlocfilehash: eed5a72cb9da95f79831784d2bb53a6d60f92988
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="3a6a1-102">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="3a6a1-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="3a6a1-103">Fournit des méthodes pour l’hôte évaluer la stratégie de liaison actuelle et de communiquer des modifications de stratégie pour un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="3a6a1-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a6a1-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3a6a1-104">Methods</span></span>  
  
|<span data-ttu-id="3a6a1-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3a6a1-105">Method</span></span>|<span data-ttu-id="3a6a1-106">Description</span><span class="sxs-lookup"><span data-stu-id="3a6a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a6a1-107">EvaluatePolicy (méthode)</span><span class="sxs-lookup"><span data-stu-id="3a6a1-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="3a6a1-108">Évalue la stratégie de liaison pour le compte de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="3a6a1-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="3a6a1-109">ModifyApplicationPolicy (méthode)</span><span class="sxs-lookup"><span data-stu-id="3a6a1-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="3a6a1-110">Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="3a6a1-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a6a1-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3a6a1-111">Requirements</span></span>  
 <span data-ttu-id="3a6a1-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a6a1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a6a1-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a6a1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a6a1-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a6a1-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a6a1-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a6a1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a6a1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a6a1-116">See Also</span></span>  
 [<span data-ttu-id="3a6a1-117">ICLRAssemblyIdentityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="3a6a1-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="3a6a1-118">IHostAssemblyStore (Interface)</span><span class="sxs-lookup"><span data-stu-id="3a6a1-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="3a6a1-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="3a6a1-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
