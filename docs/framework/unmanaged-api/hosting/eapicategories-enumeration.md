---
title: "EApiCategories, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eaff0133020fe84e58f8a130bffc8ddc2a55a19d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="e7d30-102">EApiCategories, énumération</span><span class="sxs-lookup"><span data-stu-id="e7d30-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="e7d30-103">Décrit les catégories de fonctionnalités que l’hôte peut bloquer l’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7d30-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="e7d30-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e7d30-105">Members</span></span>  
  
|<span data-ttu-id="e7d30-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e7d30-106">Member</span></span>|<span data-ttu-id="e7d30-107">Description</span><span class="sxs-lookup"><span data-stu-id="e7d30-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="e7d30-108">Spécifie que tous gérés des classes et membres qui sont couverts par d’autres `EApiCategories` champs pas s’exécuter dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="e7d30-109">Spécifie que les classes et les membres qui permettent la création, la manipulation et la destruction de processus externes doit être bloquée en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="e7d30-110">Spécifie que les classes et les membres qui permettent la création, la manipulation et la destruction de threads externes doit être bloquée en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="e7d30-111">Spécifie que les types managés et les membres qui pourraient potentiellement une fuite de mémoire d’abandon doit être bloquée en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="e7d30-112">Spécifie qu’aucune catégorie de code managé doit être bloquée en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="e7d30-113">Spécifie que l’infrastructure de sécurité du common language runtime (CLR) doit être bloquée utilisé par du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="e7d30-114">Spécifie que les classes et les membres dont les fonctions peuvent affecter le processus hébergé doit être bloquée en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="e7d30-115">Spécifie que les classes et les membres dont les fonctions peuvent affecter des threads dans le processus hébergé doit être bloquée en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="e7d30-116">Spécifie que les classes et les membres qui exposent l’état partagé doit être bloquée en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="e7d30-117">Spécifie que les classes du Common language runtime et les membres qui permettent de conserver des verrous de code utilisateur courants être bloqué de s’exécuter dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="e7d30-118">Spécifie que les classes et les membres qui autorisent ou nécessitent une interaction humaine doit être bloquée en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="e7d30-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7d30-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="e7d30-119">Remarks</span></span>  
 <span data-ttu-id="e7d30-120">Le [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) méthode prend un paramètre de type `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="e7d30-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="e7d30-121">Le `EApiCategories` énumération et la `SetProtectedCategories` méthode sont directement liés à la <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="e7d30-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e7d30-122">La classe managée est utilisée avec la <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> énumération, dont les valeurs correspondent directement à la `EApiCategories` pour marquer des types managés et les membres qui exposent des fonctions correspondant aux catégories décrites par les valeurs `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="e7d30-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d30-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e7d30-123">Requirements</span></span>  
 <span data-ttu-id="e7d30-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d30-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d30-125">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7d30-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7d30-126">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7d30-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7d30-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d30-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d30-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7d30-128">See Also</span></span>  
 [<span data-ttu-id="e7d30-129">ICLRHostProtectionManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="e7d30-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="e7d30-130">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="e7d30-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
