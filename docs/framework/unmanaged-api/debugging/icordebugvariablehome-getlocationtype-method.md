---
title: "ICorDebugVariableHome::GetLocationType (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a600f26440e29a60d776be8679d7a298d77434f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="8661e-102">ICorDebugVariableHome::GetLocationType (méthode)</span><span class="sxs-lookup"><span data-stu-id="8661e-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="8661e-103">Obtient le type d’emplacement native de la variable.</span><span class="sxs-lookup"><span data-stu-id="8661e-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8661e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8661e-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8661e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8661e-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="8661e-106">[out] Pointeur vers le type d’emplacement native de la variable.</span><span class="sxs-lookup"><span data-stu-id="8661e-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="8661e-107">Consultez le [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) énumération pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="8661e-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8661e-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8661e-108">Requirements</span></span>  
 <span data-ttu-id="8661e-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8661e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8661e-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8661e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8661e-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8661e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8661e-112">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8661e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8661e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8661e-113">See Also</span></span>  
 [<span data-ttu-id="8661e-114">Interface de ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="8661e-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="8661e-115">Énumération de VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="8661e-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
