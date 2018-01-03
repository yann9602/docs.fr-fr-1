---
title: "ICorDebugFunction::GetToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7edf1f9dadafd989197170123cb3cb470a5ea908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="bc1a1-102">ICorDebugFunction::GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="bc1a1-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="bc1a1-103">Obtient les métadonnées de jeton pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="bc1a1-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc1a1-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc1a1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bc1a1-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="bc1a1-106">[out] Un pointeur vers un `mdMethodDef` jeton qui référence les métadonnées pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="bc1a1-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1a1-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bc1a1-107">Requirements</span></span>  
 <span data-ttu-id="bc1a1-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc1a1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc1a1-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc1a1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc1a1-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc1a1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc1a1-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc1a1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
