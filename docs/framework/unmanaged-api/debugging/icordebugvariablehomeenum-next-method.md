---
title: "ICorDebugVariableHomeEnum::Next (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480317a4ec0515411f1ca8156a5bc4d06aa3f38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="c71aa-102">ICorDebugVariableHomeEnum::Next (méthode)</span><span class="sxs-lookup"><span data-stu-id="c71aa-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="c71aa-103">Obtient le nombre spécifié de [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances qui contiennent des informations sur les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="c71aa-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c71aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c71aa-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c71aa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c71aa-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c71aa-106">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="c71aa-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="c71aa-107">Un tableau de pointeurs, chacun pointant vers un [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objet qui fournit des informations sur une variable locale ou un argument d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="c71aa-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c71aa-108">[out] Le nombre d’instances réellement retournés dans les objets.</span><span class="sxs-lookup"><span data-stu-id="c71aa-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c71aa-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c71aa-109">Return Value</span></span>  
 <span data-ttu-id="c71aa-110">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="c71aa-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="c71aa-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c71aa-111">HRESULT</span></span>|<span data-ttu-id="c71aa-112">Description</span><span class="sxs-lookup"><span data-stu-id="c71aa-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c71aa-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="c71aa-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c71aa-114">Le nombre réel d’instances est récupéré, comme indiqué dans `pceltFetched`, est inférieur au nombre d’instances demandées.</span><span class="sxs-lookup"><span data-stu-id="c71aa-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c71aa-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="c71aa-115">Remarks</span></span>  
 <span data-ttu-id="c71aa-116">Le [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) méthode extrait un maximum de `celt` objets commençant à la position actuelle de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="c71aa-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="c71aa-117">Lorsque la méthode retourne, `pceltFetched` contient le nombre réel d’objets récupérés.</span><span class="sxs-lookup"><span data-stu-id="c71aa-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c71aa-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c71aa-118">Requirements</span></span>  
 <span data-ttu-id="c71aa-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c71aa-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c71aa-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c71aa-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c71aa-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c71aa-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c71aa-122">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c71aa-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71aa-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c71aa-123">See Also</span></span>  
 [<span data-ttu-id="c71aa-124">Interface de ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="c71aa-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="c71aa-125">Interface de ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="c71aa-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
