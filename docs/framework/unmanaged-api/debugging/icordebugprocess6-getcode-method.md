---
title: "ICorDebugProcess6::GetCode, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c69ce290a486960978ddaf87203328df4f392b48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="1e4af-102">ICorDebugProcess6::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="1e4af-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="1e4af-103">Obtient des informations sur le code managé à une adresse de code particulière.</span><span class="sxs-lookup"><span data-stu-id="1e4af-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e4af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e4af-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e4af-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1e4af-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="1e4af-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valeur qui spécifie l’adresse de départ du segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="1e4af-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="1e4af-107">[out] Pointeur vers l’adresse d’un objet « ICorDebugCode » représente un segment de code managé.</span><span class="sxs-lookup"><span data-stu-id="1e4af-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e4af-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="1e4af-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e4af-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1e4af-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e4af-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1e4af-110">Requirements</span></span>  
 <span data-ttu-id="1e4af-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e4af-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e4af-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e4af-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e4af-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e4af-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e4af-114">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e4af-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4af-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e4af-115">See Also</span></span>  
 [<span data-ttu-id="1e4af-116">Icordebugprocess6, Interface</span><span class="sxs-lookup"><span data-stu-id="1e4af-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="1e4af-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1e4af-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
