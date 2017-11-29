---
title: "EClrFailure, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrFailure
helpviewer_keywords: EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94358fd0626fa17f1fd6d3c365aff79f89dde467
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="1ee50-102">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="1ee50-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="1ee50-103">Décrit l’ensemble des erreurs pour lequel un hôte peut définir des actions de stratégie.</span><span class="sxs-lookup"><span data-stu-id="1ee50-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ee50-104">Syntax</span></span>  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="1ee50-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1ee50-105">Members</span></span>  
  
|<span data-ttu-id="1ee50-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1ee50-106">Member</span></span>|<span data-ttu-id="1ee50-107">Description</span><span class="sxs-lookup"><span data-stu-id="1ee50-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="1ee50-108">Une erreur s’est produite pendant une tentative d’allouer une ressource (par exemple, un thread, un bloc de mémoire ou un verrou) dans une région de code non critique.</span><span class="sxs-lookup"><span data-stu-id="1ee50-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="1ee50-109">Une erreur s’est produite pendant une tentative d’allouer une ressource (par exemple, un thread, un bloc de mémoire ou un verrou) dans une région de code critique.</span><span class="sxs-lookup"><span data-stu-id="1ee50-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="1ee50-110">Le common language runtime (CLR) n’est plus en mesure d’exécuter du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1ee50-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="1ee50-111">Désormais, les appels à toute fonction d’hébergement retournent une valeur HRESULT de HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1ee50-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="1ee50-112">Un thread n’a pas pu libérer un verrou lors du retour d’un <xref:System.AppDomain> objet.</span><span class="sxs-lookup"><span data-stu-id="1ee50-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="1ee50-113">L’hôte ne peut pas définir cet échec pour provoquer l’abandon d’un thread.</span><span class="sxs-lookup"><span data-stu-id="1ee50-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="1ee50-114">Un débordement de pile s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1ee50-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="1ee50-115">Une tentative a été effectuée pour lire ou écrire la mémoire protégée.</span><span class="sxs-lookup"><span data-stu-id="1ee50-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="1ee50-116">Non pris en charge dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ee50-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="1ee50-117">Un échec de contrat de code s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1ee50-117">A code contract failure occurred.</span></span> <span data-ttu-id="1ee50-118">Consultez [les contrats de Code](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="1ee50-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ee50-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="1ee50-119">Remarks</span></span>  
 <span data-ttu-id="1ee50-120">Consultez le [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) méthode pour obtenir la liste de [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs de l’hôte peut utiliser pour spécifier les actions de stratégie pour les conditions d’échec.</span><span class="sxs-lookup"><span data-stu-id="1ee50-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="1ee50-121">Pour plus d’informations sur les régions non critiques et de code, consultez [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="1ee50-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee50-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1ee50-122">Requirements</span></span>  
 <span data-ttu-id="1ee50-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ee50-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee50-124">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ee50-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ee50-125">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ee50-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ee50-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee50-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee50-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ee50-127">See Also</span></span>  
 [<span data-ttu-id="1ee50-128">ICLRPolicyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="1ee50-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="1ee50-129">SetActionOnFailure (méthode)</span><span class="sxs-lookup"><span data-stu-id="1ee50-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [<span data-ttu-id="1ee50-130">IHostPolicyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="1ee50-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="1ee50-131">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="1ee50-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
