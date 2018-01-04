---
title: "ICorRuntimeHost::SwitchOutLogicalThreadState, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.SwitchOutLogicalThreadState
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6302a836168f38991c7c371789d4913a3c95c16d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="a5b3d-102">ICorRuntimeHost::SwitchOutLogicalThreadState, méthode</span><span class="sxs-lookup"><span data-stu-id="a5b3d-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="a5b3d-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="a5b3d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5b3d-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5b3d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5b3d-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="a5b3d-106">[out] Cookie qui indique la fibre en cours de basculement.</span><span class="sxs-lookup"><span data-stu-id="a5b3d-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b3d-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a5b3d-107">Requirements</span></span>  
 <span data-ttu-id="a5b3d-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5b3d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b3d-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a5b3d-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5b3d-110">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5b3d-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5b3d-111">**Version du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a5b3d-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b3d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5b3d-112">See Also</span></span>  
 [<span data-ttu-id="a5b3d-113">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="a5b3d-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
