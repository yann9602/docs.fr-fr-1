---
title: "ICorRuntimeHost::LocksHeldByLogicalThread, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.LocksHeldByLogicalThread
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7875d78415d06a55c11a6b42476ff806a5cadc78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="5af55-102">ICorRuntimeHost::LocksHeldByLogicalThread, méthode</span><span class="sxs-lookup"><span data-stu-id="5af55-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="5af55-103">Récupère le nombre de verrous que le thread actif détient.</span><span class="sxs-lookup"><span data-stu-id="5af55-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="5af55-104">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="5af55-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5af55-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5af55-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5af55-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5af55-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="5af55-107">[out] Pointeur vers le nombre de verrous maintenus par le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="5af55-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5af55-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5af55-108">Requirements</span></span>  
 <span data-ttu-id="5af55-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5af55-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5af55-110">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5af55-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5af55-111">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5af55-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5af55-112">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="5af55-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af55-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5af55-113">See Also</span></span>  
 [<span data-ttu-id="5af55-114">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="5af55-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
