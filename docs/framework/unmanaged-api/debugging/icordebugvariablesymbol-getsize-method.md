---
title: "Méthode ICorDebugVariableSymbol::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99cba63edd56e0d27d5f558a77ee54ebf2629446
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="380f0-102">Méthode ICorDebugVariableSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="380f0-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="380f0-103">Obtient la taille d'une variable en octets.</span><span class="sxs-lookup"><span data-stu-id="380f0-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="380f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="380f0-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="380f0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="380f0-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="380f0-106">Pointeur vers un entier non signé 32 bits contenant la taille de la variable.</span><span class="sxs-lookup"><span data-stu-id="380f0-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="380f0-107">Notes</span><span class="sxs-lookup"><span data-stu-id="380f0-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="380f0-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="380f0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="380f0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="380f0-109">Requirements</span></span>  
 <span data-ttu-id="380f0-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="380f0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="380f0-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="380f0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="380f0-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="380f0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="380f0-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="380f0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380f0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="380f0-114">See Also</span></span>  
 [<span data-ttu-id="380f0-115">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="380f0-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="380f0-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="380f0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
