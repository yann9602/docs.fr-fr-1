---
title: "ICorThreadpool::CorGetAvailableThreads, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorGetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 56d86cd9be5e5cee8d3fb1e2f79c8379a73b975a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="8ceac-102">ICorThreadpool::CorGetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="8ceac-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="8ceac-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="8ceac-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ceac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ceac-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="8ceac-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ceac-105">Requirements</span></span>  
 <span data-ttu-id="8ceac-106">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ceac-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ceac-107">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ceac-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ceac-108">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ceac-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ceac-109">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ceac-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ceac-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ceac-110">See Also</span></span>  
 [<span data-ttu-id="8ceac-111">ICorThreadpool (Interface)</span><span class="sxs-lookup"><span data-stu-id="8ceac-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
