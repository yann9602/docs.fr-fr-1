---
title: "ICorDebugVariableHome::GetOffset (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f80a362d4b44d13c39218b9d7a0db11ef49f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="ab5b9-102">ICorDebugVariableHome::GetOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="ab5b9-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="ab5b9-103">Obtient le décalage à partir du Registre de base d’une variable.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab5b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab5b9-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab5b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab5b9-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="ab5b9-106">[out] Le décalage à partir du Registre de base.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab5b9-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ab5b9-107">Return Value</span></span>  
 <span data-ttu-id="ab5b9-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab5b9-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="ab5b9-109">Value</span><span class="sxs-lookup"><span data-stu-id="ab5b9-109">Value</span></span>|<span data-ttu-id="ab5b9-110">Description</span><span class="sxs-lookup"><span data-stu-id="ab5b9-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="ab5b9-111">La variable est dans un emplacement de mémoire relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="ab5b9-112">La variable n’est pas dans un emplacement de mémoire relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="ab5b9-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab5b9-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab5b9-113">Requirements</span></span>  
 <span data-ttu-id="ab5b9-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab5b9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab5b9-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab5b9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab5b9-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab5b9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab5b9-117">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab5b9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5b9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab5b9-118">See Also</span></span>  
 [<span data-ttu-id="ab5b9-119">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="ab5b9-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
