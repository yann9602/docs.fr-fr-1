---
title: "ICorDebugCode::GetAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20fe5f76e36eb7f5e59f650bc813aea8ad455078
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="c5d2e-102">ICorDebugCode::GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="c5d2e-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="c5d2e-103">Obtient l’adresse virtuelle relative (RVA) du segment de code représentant cette interface « ICorDebugCode ».</span><span class="sxs-lookup"><span data-stu-id="c5d2e-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5d2e-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5d2e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5d2e-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="c5d2e-106">[out] Pointeur vers l’adresse RVA du segment de code.</span><span class="sxs-lookup"><span data-stu-id="c5d2e-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d2e-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c5d2e-107">Requirements</span></span>  
 <span data-ttu-id="c5d2e-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d2e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d2e-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5d2e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5d2e-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5d2e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5d2e-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d2e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d2e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5d2e-112">See Also</span></span>  
 
