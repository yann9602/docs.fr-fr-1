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
ms.openlocfilehash: 0ea4a77b08b12c3f067d51f9dfe2c961192c3354
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="94a60-102">Méthode ICorDebugVariableSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="94a60-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="94a60-103">Obtient la taille d'une variable en octets.</span><span class="sxs-lookup"><span data-stu-id="94a60-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94a60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94a60-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94a60-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="94a60-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="94a60-106">Pointeur vers un entier non signé 32 bits contenant la taille de la variable.</span><span class="sxs-lookup"><span data-stu-id="94a60-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94a60-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="94a60-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94a60-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="94a60-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94a60-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="94a60-109">Requirements</span></span>  
 <span data-ttu-id="94a60-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94a60-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94a60-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94a60-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94a60-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94a60-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94a60-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94a60-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a60-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94a60-114">See Also</span></span>  
 [<span data-ttu-id="94a60-115">Icordebugvariablesymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="94a60-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="94a60-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="94a60-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
