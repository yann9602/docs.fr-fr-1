---
title: "EInitializeNewDomainFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EInitializeNewDomainFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EInitializeNewDomainFlags
helpviewer_keywords: EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa5c9aa050e0f5e634c43080d9caa5011a126529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="243a2-102">EInitializeNewDomainFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="243a2-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="243a2-103">Permet à l’hôte de fournir le runtime avec des informations sur l’initialisation d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="243a2-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="243a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="243a2-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="243a2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="243a2-105">Members</span></span>  
  
|<span data-ttu-id="243a2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="243a2-106">Member</span></span>|<span data-ttu-id="243a2-107">Description</span><span class="sxs-lookup"><span data-stu-id="243a2-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="243a2-108">Aucun indicateur.</span><span class="sxs-lookup"><span data-stu-id="243a2-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="243a2-109">Informe le common language runtime (CLR) que l’ordinateur hôte ne sera pas apporter des modifications à l’état de sécurité du domaine d’application dans le <xref:System.AppDomainManager.InitializeNewDomain%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="243a2-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="243a2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="243a2-110">Remarks</span></span>  
 <span data-ttu-id="243a2-111">Le [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) méthode prend un paramètre de type `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="243a2-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="243a2-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="243a2-112">Requirements</span></span>  
 <span data-ttu-id="243a2-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="243a2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="243a2-114">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="243a2-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="243a2-115">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="243a2-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="243a2-116">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="243a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243a2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="243a2-117">See Also</span></span>  
 [<span data-ttu-id="243a2-118">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="243a2-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="243a2-119">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="243a2-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
