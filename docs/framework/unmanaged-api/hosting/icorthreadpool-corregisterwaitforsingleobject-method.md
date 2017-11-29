---
title: "ICorThreadpool::CorRegisterWaitForSingleObject, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorRegisterWaitForSingleObject
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRegisterWaitForSingleObject
helpviewer_keywords:
- ICorThreadpool::CorRegisterWaitForSingleObject method [.NET Framework hosting]
- CorRegisterWaitForSingleObject method [.NET Framework hosting]
ms.assetid: cade1feb-71d2-43ed-85ca-7b2e9da12994
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72c953022514ee916e34c596eb2f504725b75ab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorthreadpoolcorregisterwaitforsingleobject-method"></a><span data-ttu-id="4ed9f-102">ICorThreadpool::CorRegisterWaitForSingleObject, méthode</span><span class="sxs-lookup"><span data-stu-id="4ed9f-102">ICorThreadpool::CorRegisterWaitForSingleObject Method</span></span>
<span data-ttu-id="4ed9f-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="4ed9f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ed9f-104">Syntax</span></span>  
  
```  
HRESULT CorRegisterWaitForSingleObject (  
    [in]  HANDLE*             phNewWaitObject,  
    [in]  HANDLE              hWaitObject,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Context,  
    [in]  ULONG               timeout,  
    [in]  BOOL                executeOnlyOnce,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4ed9f-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4ed9f-105">Requirements</span></span>  
 <span data-ttu-id="4ed9f-106">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ed9f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ed9f-107">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4ed9f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ed9f-108">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ed9f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ed9f-109">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ed9f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed9f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ed9f-110">See Also</span></span>  
 [<span data-ttu-id="4ed9f-111">ICorThreadpool (Interface)</span><span class="sxs-lookup"><span data-stu-id="4ed9f-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
