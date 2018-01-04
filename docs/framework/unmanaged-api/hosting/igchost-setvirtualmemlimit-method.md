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
ms.workload: dotnet
ms.openlocfilehash: 5fca9ee8473ed70ca5da3b5607d38f4123fd47e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="20afd-102">IGCHost::SetVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="20afd-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="20afd-103">Définit la taille maximale de mémoire virtuelle du runtime.</span><span class="sxs-lookup"><span data-stu-id="20afd-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20afd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20afd-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20afd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20afd-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="20afd-106">[in] La taille maximale, en mégaoctets, de la mémoire du runtime virtuel.</span><span class="sxs-lookup"><span data-stu-id="20afd-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20afd-107">Notes</span><span class="sxs-lookup"><span data-stu-id="20afd-107">Remarks</span></span>  
 <span data-ttu-id="20afd-108">La taille maximale de la mémoire du runtime virtuels permettre être modifiée de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="20afd-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20afd-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="20afd-109">Requirements</span></span>  
 <span data-ttu-id="20afd-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20afd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20afd-111">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="20afd-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="20afd-112">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20afd-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20afd-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20afd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20afd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20afd-114">See Also</span></span>  
 [<span data-ttu-id="20afd-115">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="20afd-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
