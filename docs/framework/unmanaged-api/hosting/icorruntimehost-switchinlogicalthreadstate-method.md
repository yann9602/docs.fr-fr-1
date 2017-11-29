---
title: "ICorRuntimeHost::SwitchInLogicalThreadState, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.SwitchInLogicalThreadState
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b17927498c5f9000d6c7c0e32d46f6f87a9c78af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="118e3-102">ICorRuntimeHost::SwitchInLogicalThreadState, méthode</span><span class="sxs-lookup"><span data-stu-id="118e3-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="118e3-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="118e3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="118e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="118e3-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="118e3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="118e3-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="118e3-106">[in] Cookie qui indique la fibre à utiliser.</span><span class="sxs-lookup"><span data-stu-id="118e3-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="118e3-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="118e3-107">Requirements</span></span>  
 <span data-ttu-id="118e3-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="118e3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="118e3-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="118e3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="118e3-110">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="118e3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="118e3-111">**Version du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="118e3-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="118e3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="118e3-112">See Also</span></span>  
 [<span data-ttu-id="118e3-113">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="118e3-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
