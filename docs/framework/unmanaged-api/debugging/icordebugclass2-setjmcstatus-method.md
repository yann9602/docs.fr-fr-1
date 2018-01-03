---
title: "ICorDebugClass2::SetJMCStatus, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fa9de4482b674173dba6a8316491507330f6376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="fff50-102">ICorDebugClass2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="fff50-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="fff50-103">Pour chaque méthode de la classe, définit une valeur qui indique si la méthode est un code défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fff50-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fff50-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fff50-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fff50-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="fff50-106">[in] La valeur `true` pour indiquer que la méthode est définie par l’utilisateur de code ; sinon, valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="fff50-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fff50-107">Notes</span><span class="sxs-lookup"><span data-stu-id="fff50-107">Remarks</span></span>  
 <span data-ttu-id="fff50-108">Un uniquement mon code (JMC) ignorera le code non défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fff50-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="fff50-109">Code défini par l’utilisateur doit être un sous-ensemble de code pouvant être débogué.</span><span class="sxs-lookup"><span data-stu-id="fff50-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="fff50-110">`SetJMCStatus`Retourne une valeur HRESULT de S_FALSE en cas d’échec définir la valeur de n’importe quelle méthode, même si la valeur pour toutes les autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="fff50-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff50-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fff50-111">Requirements</span></span>  
 <span data-ttu-id="fff50-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fff50-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff50-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fff50-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fff50-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fff50-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fff50-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fff50-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
