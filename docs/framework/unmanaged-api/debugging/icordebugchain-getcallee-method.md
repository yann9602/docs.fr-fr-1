---
title: "ICorDebugChain::GetCallee, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b584929d99e641e361de916c402a0d5723e53c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="d334b-102">ICorDebugChain::GetCallee, méthode</span><span class="sxs-lookup"><span data-stu-id="d334b-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="d334b-103">Obtient la chaîne qui a été appelée par cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="d334b-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d334b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d334b-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d334b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d334b-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="d334b-106">[out] Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne appelée.</span><span class="sxs-lookup"><span data-stu-id="d334b-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="d334b-107">Si cette chaîne est en cours d’exécution (autrement dit, si cette chaîne n’est pas en attente pour un retour de chaîne appelée), `ppChain` sera null.</span><span class="sxs-lookup"><span data-stu-id="d334b-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d334b-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d334b-108">Remarks</span></span>  
 <span data-ttu-id="d334b-109">Cette chaîne attendra la chaîne appelée à retourner avant de reprendre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d334b-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="d334b-110">La chaîne appelée peut être sur un autre thread dans le cas d’appels marshalés inter-threads.</span><span class="sxs-lookup"><span data-stu-id="d334b-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d334b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d334b-111">Requirements</span></span>  
 <span data-ttu-id="d334b-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d334b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d334b-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d334b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d334b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d334b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d334b-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d334b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
