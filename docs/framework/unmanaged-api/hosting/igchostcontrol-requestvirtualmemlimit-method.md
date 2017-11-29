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
ms.openlocfilehash: 4892cf5dc3a3663f1bccc95d1975bfe96277faa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="3d6a5-102">IGCHostControl::RequestVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="3d6a5-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="3d6a5-103">Demande à l’hôte de modifier les limites de mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d6a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d6a5-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d6a5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d6a5-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="3d6a5-106">[in] La taille de la mémoire à allouer.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="3d6a5-107">[dans, out] Pointeur vers la taille réelle de la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d6a5-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3d6a5-108">Requirements</span></span>  
 <span data-ttu-id="3d6a5-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d6a5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d6a5-110">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d6a5-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d6a5-111">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d6a5-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d6a5-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d6a5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6a5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d6a5-113">See Also</span></span>  
 [<span data-ttu-id="3d6a5-114">IGCHostControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="3d6a5-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
