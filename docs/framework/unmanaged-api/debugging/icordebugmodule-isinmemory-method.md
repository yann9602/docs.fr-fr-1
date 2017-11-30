---
title: "ICorDebugModule::IsInMemory, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsInMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58f7964faee19f85c83d1b9b1c3e176354ae9588
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="d4239-102">ICorDebugModule::IsInMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="d4239-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="d4239-103">Obtient une valeur qui indique si ce module existe uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d4239-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4239-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4239-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4239-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4239-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="d4239-106">[out] `true` si ce module existe uniquement en mémoire ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="d4239-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4239-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="d4239-107">Remarks</span></span>  
 <span data-ttu-id="d4239-108">Le common language runtime (CLR) prend en charge le chargement de modules à partir de flux bruts d’octets.</span><span class="sxs-lookup"><span data-stu-id="d4239-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="d4239-109">Ces modules sont appelés *en mémoire modules* et n’existent pas sur le disque.</span><span class="sxs-lookup"><span data-stu-id="d4239-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4239-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d4239-110">Requirements</span></span>  
 <span data-ttu-id="d4239-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4239-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4239-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4239-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4239-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4239-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4239-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4239-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4239-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4239-115">See Also</span></span>  
    
 
