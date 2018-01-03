---
title: "ICorDebugChain::GetActiveFrame, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7498e031b74bd904b908342b663e4421432e6d95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="c6e19-102">ICorDebugChain::GetActiveFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="c6e19-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="c6e19-103">Obtient l’active (autrement dit, la plus récente) frame sur la chaîne.</span><span class="sxs-lookup"><span data-stu-id="c6e19-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6e19-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6e19-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6e19-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="c6e19-106">[out] Un pointeur vers l’adresse d’un objet ICorDebugFrame qui représente l’actif (autrement dit, la plus récente) frame sur la chaîne.</span><span class="sxs-lookup"><span data-stu-id="c6e19-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6e19-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c6e19-107">Remarks</span></span>  
 <span data-ttu-id="c6e19-108">Si aucun frame de pile managé n’est disponible, `ppFrame` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="c6e19-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="c6e19-109">Si le frame actif n’est pas disponible, l’appel réussi et `ppFrame` sera null.</span><span class="sxs-lookup"><span data-stu-id="c6e19-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="c6e19-110">Cadres active ne sera pas disponibles pour les chaînes initiées en raison de CHAIN_ENTER_UNMANAGED et pour certaines chaînes initiées en raison de CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="c6e19-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="c6e19-111">Consultez l’énumération CorDebugChainReason.</span><span class="sxs-lookup"><span data-stu-id="c6e19-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e19-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c6e19-112">Requirements</span></span>  
 <span data-ttu-id="c6e19-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6e19-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6e19-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6e19-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6e19-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6e19-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6e19-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e19-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
