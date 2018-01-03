---
title: "ICorDebugType2::GetTypeID (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d18aa8210ea90736c0757e2587aab4ff143dcdad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="49bdd-102">ICorDebugType2::GetTypeID (méthode)</span><span class="sxs-lookup"><span data-stu-id="49bdd-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="49bdd-103">Obtient un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pour ce type.</span><span class="sxs-lookup"><span data-stu-id="49bdd-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49bdd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49bdd-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49bdd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49bdd-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="49bdd-106">[out] Un pointeur vers le [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pour ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="49bdd-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49bdd-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="49bdd-107">Return Value</span></span>  
 <span data-ttu-id="49bdd-108">La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="49bdd-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="49bdd-109">Le `HRESULT` codes incluent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="49bdd-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="49bdd-110">Code de retour</span><span class="sxs-lookup"><span data-stu-id="49bdd-110">Return code</span></span>|<span data-ttu-id="49bdd-111">Description</span><span class="sxs-lookup"><span data-stu-id="49bdd-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="49bdd-112">La méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="49bdd-112">Method succeeded.</span></span> <span data-ttu-id="49bdd-113">La méthode a récupéré valide [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="49bdd-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="49bdd-114">Le type n’a pas été chargé.</span><span class="sxs-lookup"><span data-stu-id="49bdd-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="49bdd-115">Le type n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="49bdd-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49bdd-116">Notes</span><span class="sxs-lookup"><span data-stu-id="49bdd-116">Remarks</span></span>  
 <span data-ttu-id="49bdd-117">Cette méthode fournit un mappage à partir de ICorDebugType, ce qui représente un type qui peut ou ont ne peut-être pas été chargé dans l’exécution, à un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), qui sert un opaque gérer qui identifie un type chargé dans le runtime.</span><span class="sxs-lookup"><span data-stu-id="49bdd-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="49bdd-118">Lorsque le type représentant le ICorDebugType n’a pas encore été chargé, cette méthode retourne `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="49bdd-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="49bdd-119">Si le type n’est pas pris en charge, elle retourne `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="49bdd-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49bdd-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="49bdd-120">Requirements</span></span>  
 <span data-ttu-id="49bdd-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49bdd-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49bdd-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49bdd-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49bdd-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49bdd-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49bdd-124">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49bdd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bdd-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49bdd-125">See Also</span></span>  
 [<span data-ttu-id="49bdd-126">ICorDebugType2, interface</span><span class="sxs-lookup"><span data-stu-id="49bdd-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
