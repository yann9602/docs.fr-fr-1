---
title: "ICorDebugILCode::GetEHClauses, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode.GetEHClauses
api_location: mscordbi.dll
api_type: COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32b3a7bf7edaf15e44ea65e2d3b4f5037add8d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="a66e1-102">ICorDebugILCode::GetEHClauses, méthode</span><span class="sxs-lookup"><span data-stu-id="a66e1-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="a66e1-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="a66e1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a66e1-104">Retourne un pointeur vers une liste de clauses de gestion des exceptions qui sont définies pour ce langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="a66e1-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66e1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a66e1-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a66e1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a66e1-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="a66e1-107">[en entrée] La capacité de stockage du tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="a66e1-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="a66e1-108">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="a66e1-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="a66e1-109">[en sortie] Le nombre de clauses à propos desquelles des informations sont écrites dans le tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="a66e1-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="a66e1-110">clauses</span><span class="sxs-lookup"><span data-stu-id="a66e1-110">clauses</span></span>  
 <span data-ttu-id="a66e1-111">[out] Un tableau de [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) les objets qui contiennent des informations sur les clauses définies pour ce langage intermédiaire de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="a66e1-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a66e1-112">Notes</span><span class="sxs-lookup"><span data-stu-id="a66e1-112">Remarks</span></span>  
 <span data-ttu-id="a66e1-113">Si `cClauses` est égal à 0 et `pcClauses` est non -**null**, `pcClauses` est défini sur le nombre d’exceptions disponibles, la gestion des clauses.</span><span class="sxs-lookup"><span data-stu-id="a66e1-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="a66e1-114">Si `cClauses` est différent de zéro, il représente la capacité de stockage du tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="a66e1-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="a66e1-115">Quand la méthode se termine, `clauses` contient un maximum de `cClauses` éléments et `pcClauses` est défini avec le nombre de clauses réellement écrites dans le tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="a66e1-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a66e1-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a66e1-116">Requirements</span></span>  
 <span data-ttu-id="a66e1-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a66e1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a66e1-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a66e1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a66e1-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a66e1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a66e1-120">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a66e1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66e1-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a66e1-121">See Also</span></span>  
 [<span data-ttu-id="a66e1-122">ICorDebugILCode, interface</span><span class="sxs-lookup"><span data-stu-id="a66e1-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="a66e1-123">CorDebugEHClause, structure</span><span class="sxs-lookup"><span data-stu-id="a66e1-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [<span data-ttu-id="a66e1-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a66e1-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
