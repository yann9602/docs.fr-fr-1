---
title: "EClrUnhandledException, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrUnhandledException
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrUnhandledException
helpviewer_keywords: EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8fcc9254499724d94153c445943fdaf78d12a10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="40330-102">EClrUnhandledException, énumération</span><span class="sxs-lookup"><span data-stu-id="40330-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="40330-103">Décrit les options disponibles pour la gestion des exceptions qui ne sont pas gérées dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="40330-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40330-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40330-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="40330-105">Membres</span><span class="sxs-lookup"><span data-stu-id="40330-105">Members</span></span>  
  
|<span data-ttu-id="40330-106">Membre</span><span class="sxs-lookup"><span data-stu-id="40330-106">Member</span></span>|<span data-ttu-id="40330-107">Description</span><span class="sxs-lookup"><span data-stu-id="40330-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="40330-108">Spécifie que le comportement par défaut se produit.</span><span class="sxs-lookup"><span data-stu-id="40330-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="40330-109">Le processus est détruit.</span><span class="sxs-lookup"><span data-stu-id="40330-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="40330-110">Spécifie que le common language runtime (CLR) ignore les exceptions non gérées et permet à l’hôte de déterminer toute action supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="40330-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40330-111">Notes</span><span class="sxs-lookup"><span data-stu-id="40330-111">Remarks</span></span>  
 <span data-ttu-id="40330-112">Pour spécifier que le CLR se comportent comme les versions antérieures, utilisez le `eHostDeterminedPolicy` membre.</span><span class="sxs-lookup"><span data-stu-id="40330-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40330-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="40330-113">Requirements</span></span>  
 <span data-ttu-id="40330-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40330-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40330-115">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40330-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40330-116">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40330-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40330-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40330-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40330-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40330-118">See Also</span></span>  
 [<span data-ttu-id="40330-119">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="40330-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="40330-120">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="40330-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="40330-121">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="40330-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="40330-122">SetUnhandledExceptionPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="40330-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="40330-123">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="40330-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="40330-124">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="40330-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
