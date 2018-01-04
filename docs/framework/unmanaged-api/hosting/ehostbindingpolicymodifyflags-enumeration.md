---
title: "EHostBindingPolicyModifyFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EHostBindingPolicyModifyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EHostBindingPolicyModifyFlags
helpviewer_keywords: EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb985cf2f34719b3aed9397155bd9d538b57dc3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="d6be0-102">EHostBindingPolicyModifyFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="d6be0-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="d6be0-103">Permet à l’hôte spécifier le type de redirection que le common language runtime (CLR) doit effectuer lors de l’application des modifications de la stratégie à partir d’un assembly source vers un assembly cible.</span><span class="sxs-lookup"><span data-stu-id="d6be0-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6be0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6be0-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d6be0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d6be0-105">Members</span></span>  
  
|<span data-ttu-id="d6be0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d6be0-106">Member</span></span>|<span data-ttu-id="d6be0-107">Description</span><span class="sxs-lookup"><span data-stu-id="d6be0-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="d6be0-108">Spécifie que le CLR doit chaîner les valeurs de stratégie de l’assembly source vers ceux de l’assembly cible.</span><span class="sxs-lookup"><span data-stu-id="d6be0-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="d6be0-109">Spécifie que le CLR exécute l’action par défaut.</span><span class="sxs-lookup"><span data-stu-id="d6be0-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="d6be0-110">Spécifie que le CLR définit les valeurs de stratégie de l’assembly cible pour les valeurs maximales.</span><span class="sxs-lookup"><span data-stu-id="d6be0-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="d6be0-111">Spécifie que le CLR doit remplacer les valeurs de stratégie de l’assembly cible avec celles de l’assembly source.</span><span class="sxs-lookup"><span data-stu-id="d6be0-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6be0-112">Notes</span><span class="sxs-lookup"><span data-stu-id="d6be0-112">Remarks</span></span>  
 <span data-ttu-id="d6be0-113">Le [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) méthode prend un paramètre de type `EHostBindingPolicyModifyFlags`.</span><span class="sxs-lookup"><span data-stu-id="d6be0-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6be0-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d6be0-114">Requirements</span></span>  
 <span data-ttu-id="d6be0-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6be0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6be0-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6be0-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6be0-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6be0-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6be0-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6be0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6be0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6be0-119">See Also</span></span>  
 [<span data-ttu-id="d6be0-120">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="d6be0-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="d6be0-121">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="d6be0-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
