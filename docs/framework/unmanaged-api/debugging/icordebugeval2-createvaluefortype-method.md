---
title: "ICorDebugEval2::CreateValueForType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CreateValueForType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc2760b1c303141372aed824bda71ebdae8ffe0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="a63e0-102">ICorDebugEval2::CreateValueForType, méthode</span><span class="sxs-lookup"><span data-stu-id="a63e0-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="a63e0-103">Obtient un pointeur vers un nouvel ICorDebugValue du type spécifié, avec une valeur initiale de zéro ou null.</span><span class="sxs-lookup"><span data-stu-id="a63e0-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63e0-104">Syntax</span></span>  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a63e0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a63e0-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="a63e0-106">[in] Pointeur vers un objet ICorDebugType qui représente le type.</span><span class="sxs-lookup"><span data-stu-id="a63e0-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a63e0-107">[out] Pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente la valeur.</span><span class="sxs-lookup"><span data-stu-id="a63e0-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a63e0-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="a63e0-108">Remarks</span></span>  
 <span data-ttu-id="a63e0-109">`CreateValueForType`généralise [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) en vous permettant de spécifier un type d’objet arbitraire, y compris les types construits comme `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="a63e0-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="a63e0-110">Il est le seul objectif de cette méthode pour générer une valeur qui peut être passée à une évaluation de fonction.</span><span class="sxs-lookup"><span data-stu-id="a63e0-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="a63e0-111">Le type doit être une classe ou un type valeur.</span><span class="sxs-lookup"><span data-stu-id="a63e0-111">The type must be a class or a value type.</span></span> <span data-ttu-id="a63e0-112">Vous ne pouvez pas utiliser cette méthode pour créer des valeurs de chaîne ou des valeurs de tableau.</span><span class="sxs-lookup"><span data-stu-id="a63e0-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a63e0-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a63e0-113">Requirements</span></span>  
 <span data-ttu-id="a63e0-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a63e0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a63e0-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a63e0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a63e0-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a63e0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a63e0-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a63e0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
