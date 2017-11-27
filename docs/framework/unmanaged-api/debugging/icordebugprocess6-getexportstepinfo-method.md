---
title: "ICorDebugProcess6::GetExportStepInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbb0e1cf904675005522002596476aec996124b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="87e62-102">ICorDebugProcess6::GetExportStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="87e62-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="87e62-103">Fournit des informations sur les fonctions exportées du runtime pour faciliter l'exécution pas à pas du code managé.</span><span class="sxs-lookup"><span data-stu-id="87e62-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87e62-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87e62-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="87e62-105">Parameters</span></span>  
 <span data-ttu-id="87e62-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="87e62-106">pszExportName</span></span>  
 <span data-ttu-id="87e62-107">[in] Nom d'une fonction exportée du runtime tel qu'écrit dans la table d'exportation PE.</span><span class="sxs-lookup"><span data-stu-id="87e62-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="87e62-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="87e62-108">invokeKind</span></span>  
 <span data-ttu-id="87e62-109">[out] Un pointeur vers un membre de la [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) énumération qui décrit la façon dont la fonction exportée appelle du code managé.</span><span class="sxs-lookup"><span data-stu-id="87e62-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="87e62-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="87e62-110">invokePurpose</span></span>  
 <span data-ttu-id="87e62-111">[out] Un pointeur vers un membre de la [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) énumération qui décrit la raison pour laquelle la fonction exportée appelle du code managé.</span><span class="sxs-lookup"><span data-stu-id="87e62-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87e62-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="87e62-112">Return Value</span></span>  
 <span data-ttu-id="87e62-113">La méthode peut retourner les valeurs répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="87e62-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="87e62-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="87e62-114">Return value</span></span>|<span data-ttu-id="87e62-115">Description</span><span class="sxs-lookup"><span data-stu-id="87e62-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="87e62-116">L'appel de méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="87e62-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="87e62-117">`pInvokeKind`ou `pInvokePurpose` est **null**.</span><span class="sxs-lookup"><span data-stu-id="87e62-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="87e62-118">Autres valeurs `HRESULT` indiquant un échec.</span><span class="sxs-lookup"><span data-stu-id="87e62-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="87e62-119">Selon le cas</span><span class="sxs-lookup"><span data-stu-id="87e62-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87e62-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="87e62-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87e62-121">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="87e62-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e62-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="87e62-122">Requirements</span></span>  
 <span data-ttu-id="87e62-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87e62-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e62-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87e62-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87e62-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87e62-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87e62-126">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e62-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e62-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87e62-127">See Also</span></span>  
 [<span data-ttu-id="87e62-128">Icordebugprocess6, Interface</span><span class="sxs-lookup"><span data-stu-id="87e62-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="87e62-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="87e62-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
