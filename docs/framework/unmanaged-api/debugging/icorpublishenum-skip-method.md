---
title: "ICorPublishEnum::Skip, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.Skip
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f75681237ff00b61cf584fb99c7ee6bbda6df48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="12ed4-102">ICorPublishEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="12ed4-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="12ed4-103">Déplace le curseur vers l’avant dans l’énumération par le nombre spécifié d’éléments.</span><span class="sxs-lookup"><span data-stu-id="12ed4-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ed4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12ed4-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12ed4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12ed4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="12ed4-106">[in] Le nombre d’éléments permettant de déplacer le curseur vers le bas.</span><span class="sxs-lookup"><span data-stu-id="12ed4-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12ed4-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="12ed4-107">Requirements</span></span>  
 <span data-ttu-id="12ed4-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12ed4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ed4-109">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="12ed4-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="12ed4-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12ed4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12ed4-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12ed4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ed4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12ed4-112">See Also</span></span>  
 [<span data-ttu-id="12ed4-113">ICorPublishEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="12ed4-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
