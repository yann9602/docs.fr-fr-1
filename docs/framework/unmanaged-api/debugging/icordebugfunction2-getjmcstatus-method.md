---
title: "ICorDebugFunction2::GetJMCStatus, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.GetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d877b534ca2501117153047858a1a1f2736bdd4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="6d202-102">ICorDebugFunction2::GetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="6d202-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="6d202-103">Obtient une valeur qui indique si la fonction qui est représentée par cet objet ICorDebugFunction2 est marquée comme du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6d202-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d202-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d202-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d202-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d202-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="6d202-106">[out] Un pointeur vers une valeur booléenne qui est `true`, si cette fonction est marquée comme du code utilisateur ; sinon, la valeur est `false`.</span><span class="sxs-lookup"><span data-stu-id="6d202-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d202-107">Notes</span><span class="sxs-lookup"><span data-stu-id="6d202-107">Remarks</span></span>  
 <span data-ttu-id="6d202-108">Si la fonction représentée par ce `ICorDebugFunction2` ne peut pas être débogué `pbIsJustMyCode` sera toujours `false`.</span><span class="sxs-lookup"><span data-stu-id="6d202-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d202-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6d202-109">Requirements</span></span>  
 <span data-ttu-id="6d202-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d202-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d202-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d202-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d202-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d202-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d202-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d202-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
