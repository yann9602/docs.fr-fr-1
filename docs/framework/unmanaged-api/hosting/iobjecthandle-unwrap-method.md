---
title: "IObjectHandle::Unwrap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IObjectHandle.Unwrap
api_location: mscoree.dll
api_type: COM
f1_keywords: Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d4ff12674fefbde6afbbe76cb411dbbe33d2187
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="cc093-102">IObjectHandle::Unwrap, méthode</span><span class="sxs-lookup"><span data-stu-id="cc093-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="cc093-103">Désencapsule un objet marshalé-par-valeur à partir de l’indirection.</span><span class="sxs-lookup"><span data-stu-id="cc093-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc093-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc093-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc093-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc093-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="cc093-106">[out] Pointeur vers l’objet à désencapsuler.</span><span class="sxs-lookup"><span data-stu-id="cc093-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc093-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cc093-107">Requirements</span></span>  
 <span data-ttu-id="cc093-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc093-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc093-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc093-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc093-110">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc093-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc093-111">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc093-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc093-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc093-112">See Also</span></span>  
 
