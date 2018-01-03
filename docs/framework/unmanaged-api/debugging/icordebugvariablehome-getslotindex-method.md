---
title: "ICorDebugVariableHome::GetSlotIndex (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetSlotIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ff62b79fbbb0896941730797473209872e6bfc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="08f6f-102">ICorDebugVariableHome::GetSlotIndex (méthode)</span><span class="sxs-lookup"><span data-stu-id="08f6f-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="08f6f-103">Obtient l’index d’emplacement géré d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="08f6f-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08f6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08f6f-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08f6f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08f6f-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="08f6f-106">[out] Pointeur vers l’index d’emplacement d’une variable locale.</span><span class="sxs-lookup"><span data-stu-id="08f6f-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08f6f-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="08f6f-107">Return Value</span></span>  
 <span data-ttu-id="08f6f-108">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="08f6f-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="08f6f-109">Value</span><span class="sxs-lookup"><span data-stu-id="08f6f-109">Value</span></span>|<span data-ttu-id="08f6f-110">Description</span><span class="sxs-lookup"><span data-stu-id="08f6f-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="08f6f-111">L’appel de méthode a retourné une valeur de l’index de l’emplacement dans `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="08f6f-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="08f6f-112">En cours [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance représente un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="08f6f-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08f6f-113">Notes</span><span class="sxs-lookup"><span data-stu-id="08f6f-113">Remarks</span></span>  
 <span data-ttu-id="08f6f-114">L’index d’emplacement peut être utilisé pour récupérer les métadonnées pour cette variable locale.</span><span class="sxs-lookup"><span data-stu-id="08f6f-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08f6f-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08f6f-115">Requirements</span></span>  
 <span data-ttu-id="08f6f-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08f6f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08f6f-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08f6f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08f6f-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08f6f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08f6f-119">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08f6f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f6f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08f6f-120">See Also</span></span>  
 [<span data-ttu-id="08f6f-121">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="08f6f-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
