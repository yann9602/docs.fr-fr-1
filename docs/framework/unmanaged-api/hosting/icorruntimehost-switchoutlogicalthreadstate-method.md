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
ms.openlocfilehash: 9eed11dd0a5ebd30952946f640957e9960485524
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="662cc-102">ICorRuntimeHost::SwitchOutLogicalThreadState, méthode</span><span class="sxs-lookup"><span data-stu-id="662cc-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="662cc-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="662cc-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="662cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="662cc-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="662cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="662cc-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="662cc-106">[out] Cookie qui indique la fibre en cours de basculement.</span><span class="sxs-lookup"><span data-stu-id="662cc-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="662cc-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="662cc-107">Requirements</span></span>  
 <span data-ttu-id="662cc-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="662cc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="662cc-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="662cc-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="662cc-110">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="662cc-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="662cc-111">**Version du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="662cc-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662cc-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="662cc-112">See Also</span></span>  
 [<span data-ttu-id="662cc-113">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="662cc-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
