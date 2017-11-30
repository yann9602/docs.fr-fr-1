---
title: "ICorDebugFunction2::SetJMCStatus, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ecbcd5b8171a169fbfdd7175d3d9dfbbcb3855f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="5b2a8-102">ICorDebugFunction2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="5b2a8-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="5b2a8-103">Marque la fonction représentée par ICorDebugFunction2 pour uniquement mon Code pas à pas détaillé.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b2a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b2a8-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b2a8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b2a8-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="5b2a8-106">[in] La valeur `true` pour marquer la fonction en tant que code utilisateur ; sinon, valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="5b2a8-107">Valeurs de retour</span><span class="sxs-lookup"><span data-stu-id="5b2a8-107">Return Values</span></span>  
  
|<span data-ttu-id="5b2a8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b2a8-108">HRESULT</span></span>|<span data-ttu-id="5b2a8-109">Description</span><span class="sxs-lookup"><span data-stu-id="5b2a8-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5b2a8-110">La fonction a été marquée avec succès.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="5b2a8-111">La fonction n’a pas pu être marquée comme du code utilisateur, car il ne peut pas être débogué.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b2a8-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="5b2a8-112">Remarks</span></span>  
 <span data-ttu-id="5b2a8-113">Une exécution pas à pas uniquement mon Code ignorera le code non-utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="5b2a8-114">Code utilisateur doit être un sous-ensemble de code pouvant être débogué.</span><span class="sxs-lookup"><span data-stu-id="5b2a8-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b2a8-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5b2a8-115">Requirements</span></span>  
 <span data-ttu-id="5b2a8-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b2a8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b2a8-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b2a8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b2a8-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b2a8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b2a8-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b2a8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
