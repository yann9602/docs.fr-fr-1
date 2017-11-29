---
title: "ICorDebugType::GetClass, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be9999cd0dd8db5439dd41e51429841666597b16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="58aee-102">ICorDebugType::GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="58aee-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="58aee-103">Obtient un pointeur d’interface ICorDebugClass qui représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="58aee-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58aee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58aee-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58aee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58aee-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="58aee-106">[out] Un pointeur vers l’adresse d’un `ICorDebugClass` interface qui représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="58aee-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58aee-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="58aee-107">Remarks</span></span>  
 <span data-ttu-id="58aee-108">`GetClass`peut être appelée uniquement sous certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="58aee-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="58aee-109">Appelez [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) avant d’appeler `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="58aee-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="58aee-110">Si `ICorDebugType::GetType` retourne une valeur CorElementType ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` peut être appelée pour obtenir le type non instancié pour un type générique.</span><span class="sxs-lookup"><span data-stu-id="58aee-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58aee-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="58aee-111">Requirements</span></span>  
 <span data-ttu-id="58aee-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58aee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58aee-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58aee-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58aee-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58aee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58aee-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58aee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
