---
title: "IGCHost::SetVirtualMemLimit, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.SetVirtualMemLimit
api_location: mscoree.dll
api_type: COM
f1_keywords: SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff3b5a8ba559530561503a3678a37ac0b9480907
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="459cf-102">IGCHost::SetVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="459cf-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="459cf-103">Définit la taille maximale de mémoire virtuelle du runtime.</span><span class="sxs-lookup"><span data-stu-id="459cf-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="459cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="459cf-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="459cf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="459cf-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="459cf-106">[in] La taille maximale, en mégaoctets, de la mémoire du runtime virtuel.</span><span class="sxs-lookup"><span data-stu-id="459cf-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="459cf-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="459cf-107">Remarks</span></span>  
 <span data-ttu-id="459cf-108">La taille maximale de la mémoire du runtime virtuels permettre être modifiée de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="459cf-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="459cf-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="459cf-109">Requirements</span></span>  
 <span data-ttu-id="459cf-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="459cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="459cf-111">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="459cf-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="459cf-112">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="459cf-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="459cf-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="459cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459cf-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="459cf-114">See Also</span></span>  
 [<span data-ttu-id="459cf-115">IGCHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="459cf-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
