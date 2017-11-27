---
title: "ICorDebugVariableHome::GetRegister (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetRegister
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f16e4bfe4767e1b49d7dacf0481e8911a90e178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="d19a3-102">ICorDebugVariableHome::GetRegister (méthode)</span><span class="sxs-lookup"><span data-stu-id="d19a3-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="d19a3-103">Obtient le Registre qui contient une variable avec un type d’emplacement de `VLT_REGISTER`et le Registre de base pour une variable avec un type d’emplacement de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="d19a3-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d19a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d19a3-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d19a3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d19a3-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="d19a3-106">[out] Une valeur d’énumération CorDebugRegister qui indique le Registre pour une variable avec un type d’emplacement de `VLT_REGISTER`et le Registre de base pour une variable avec un type d’emplacement de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="d19a3-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d19a3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d19a3-107">Return Value</span></span>  
 <span data-ttu-id="d19a3-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="d19a3-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="d19a3-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="d19a3-109">Value</span></span>|<span data-ttu-id="d19a3-110">Description</span><span class="sxs-lookup"><span data-stu-id="d19a3-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d19a3-111">La variable est dans le Registre indiqué par le `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="d19a3-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d19a3-112">La variable n’est pas dans un Registre ou un emplacement relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="d19a3-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d19a3-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d19a3-113">Requirements</span></span>  
 <span data-ttu-id="d19a3-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d19a3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d19a3-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d19a3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d19a3-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d19a3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d19a3-117">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d19a3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d19a3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d19a3-118">See Also</span></span>  
 [<span data-ttu-id="d19a3-119">Énumération de VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="d19a3-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="d19a3-120">Interface de ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="d19a3-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
