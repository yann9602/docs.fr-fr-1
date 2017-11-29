---
title: "ICorDebugProcess5::GetTypeFields, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeFields
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a64e754a77c7d730d921f8a8c1547dd18b66d77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="d98be-102">ICorDebugProcess5::GetTypeFields, méthode</span><span class="sxs-lookup"><span data-stu-id="d98be-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="d98be-103">Fournit des informations sur les champs qui appartiennent à un type.</span><span class="sxs-lookup"><span data-stu-id="d98be-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d98be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d98be-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d98be-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d98be-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="d98be-106">[in] L’identificateur du type dont les informations de champ sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="d98be-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="d98be-107">[in] Le nombre de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objets dont les informations de champ doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="d98be-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="d98be-108">[out] Un tableau de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) des objets qui fournissent des informations sur les champs qui appartiennent au type.</span><span class="sxs-lookup"><span data-stu-id="d98be-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="d98be-109">[out] Un pointeur vers le nombre de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objets inclus dans `fields`.</span><span class="sxs-lookup"><span data-stu-id="d98be-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d98be-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="d98be-110">Remarks</span></span>  
 <span data-ttu-id="d98be-111">Le `celt` paramètre qui spécifie le nombre de champs dont la méthode utilise pour renseigner les informations de champ `fields`, doit correspondre à la valeur de la `COR_TYPE_LAYOUT::numFields` champ.</span><span class="sxs-lookup"><span data-stu-id="d98be-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d98be-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d98be-112">Requirements</span></span>  
 <span data-ttu-id="d98be-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d98be-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d98be-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d98be-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d98be-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d98be-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d98be-116">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d98be-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d98be-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d98be-117">See Also</span></span>  
 [<span data-ttu-id="d98be-118">Icordebugprocess5, Interface</span><span class="sxs-lookup"><span data-stu-id="d98be-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="d98be-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d98be-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
