---
title: "ICorDebugVariableHome::GetArgumentIndex (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetArgumentIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 739d4d787858f64871269ea9bd467bc49424fbae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="9fd97-102">ICorDebugVariableHome::GetArgumentIndex (méthode)</span><span class="sxs-lookup"><span data-stu-id="9fd97-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="9fd97-103">Obtient l’index d’un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="9fd97-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fd97-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fd97-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fd97-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fd97-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="9fd97-106">[out] Pointeur vers l’index de l’argument.</span><span class="sxs-lookup"><span data-stu-id="9fd97-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fd97-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9fd97-107">Return Value</span></span>  
 <span data-ttu-id="9fd97-108">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="9fd97-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="9fd97-109">Value</span><span class="sxs-lookup"><span data-stu-id="9fd97-109">Value</span></span>|<span data-ttu-id="9fd97-110">Description</span><span class="sxs-lookup"><span data-stu-id="9fd97-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="9fd97-111">L’appel de méthode a retourné un index d’argument valide.</span><span class="sxs-lookup"><span data-stu-id="9fd97-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="9fd97-112">En cours [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance représente une variable locale.</span><span class="sxs-lookup"><span data-stu-id="9fd97-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fd97-113">Notes</span><span class="sxs-lookup"><span data-stu-id="9fd97-113">Remarks</span></span>  
 <span data-ttu-id="9fd97-114">L’index de l’argument peut être utilisé pour récupérer des métadonnées pour cet argument.</span><span class="sxs-lookup"><span data-stu-id="9fd97-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fd97-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9fd97-115">Requirements</span></span>  
 <span data-ttu-id="9fd97-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fd97-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fd97-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fd97-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fd97-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fd97-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fd97-119">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fd97-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd97-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fd97-120">See Also</span></span>  
 [<span data-ttu-id="9fd97-121">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="9fd97-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
