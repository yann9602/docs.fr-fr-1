---
title: "ICorDebugChain::IsManaged, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fe5736a1ca420eb361e062743ed93982e7ec3f29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="ce4c4-102">ICorDebugChain::IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="ce4c4-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="ce4c4-103">Obtient une valeur qui indique si cette chaîne est en cours d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="ce4c4-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce4c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce4c4-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce4c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce4c4-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="ce4c4-106">[out] `true` si cette chaîne est en cours d’exécution du code managé ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="ce4c4-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce4c4-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce4c4-107">Requirements</span></span>  
 <span data-ttu-id="ce4c4-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce4c4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce4c4-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce4c4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce4c4-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce4c4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce4c4-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce4c4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
