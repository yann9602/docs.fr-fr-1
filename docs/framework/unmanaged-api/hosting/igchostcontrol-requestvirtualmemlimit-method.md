---
title: "IGCHostControl::RequestVirtualMemLimit, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHostControl.RequestVirtualMemLimit
api_location: mscoree.dll
api_type: COM
f1_keywords: RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a14cb0d2d34db4ea0e5f9abf6fba6efc5e5a950c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="46d37-102">IGCHostControl::RequestVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="46d37-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="46d37-103">Demande à l’hôte de modifier les limites de mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="46d37-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46d37-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46d37-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46d37-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="46d37-106">[in] La taille de la mémoire à allouer.</span><span class="sxs-lookup"><span data-stu-id="46d37-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="46d37-107">[dans, out] Pointeur vers la taille réelle de la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="46d37-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46d37-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="46d37-108">Requirements</span></span>  
 <span data-ttu-id="46d37-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46d37-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46d37-110">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="46d37-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46d37-111">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46d37-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46d37-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46d37-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d37-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46d37-113">See Also</span></span>  
 [<span data-ttu-id="46d37-114">IGCHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="46d37-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
