---
title: "ICorDebugAssembly2::IsFullyTrusted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly2.IsFullyTrusted
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19058308876f80afdbaec73583242aa8ad3c33cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="eedac-102">ICorDebugAssembly2::IsFullyTrusted, méthode</span><span class="sxs-lookup"><span data-stu-id="eedac-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="eedac-103">Obtient une valeur qui indique si l’assembly a été accordé une confiance totale par le système de sécurité du runtime.</span><span class="sxs-lookup"><span data-stu-id="eedac-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eedac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eedac-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eedac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eedac-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="eedac-106">[out] `true` si l’assembly a été accordé à une confiance totale par le système de sécurité du runtime ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="eedac-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eedac-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="eedac-107">Remarks</span></span>  
 <span data-ttu-id="eedac-108">Cette méthode retourne un HRESULT de CORDBG_E_NOTREADY si la stratégie de sécurité de l’assembly n'a pas encore été résolue, autrement dit, si aucun code de l’assembly a encore été exécuté.</span><span class="sxs-lookup"><span data-stu-id="eedac-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eedac-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eedac-109">Requirements</span></span>  
 <span data-ttu-id="eedac-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eedac-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eedac-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eedac-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eedac-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eedac-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eedac-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eedac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
