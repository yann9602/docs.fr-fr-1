---
title: ICorDebugVariableSymbol, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 89bae73e9dfb729e26f54dc7874418163870dc27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="5ff37-102">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="5ff37-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="5ff37-103">Récupère les informations de symbole de débogage pour une variable.</span><span class="sxs-lookup"><span data-stu-id="5ff37-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ff37-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5ff37-104">Methods</span></span>  
  
|<span data-ttu-id="5ff37-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5ff37-105">Method</span></span>|<span data-ttu-id="5ff37-106">Description</span><span class="sxs-lookup"><span data-stu-id="5ff37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ff37-107">GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ff37-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="5ff37-108">Obtient le nom d'une variable.</span><span class="sxs-lookup"><span data-stu-id="5ff37-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="5ff37-109">GetSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ff37-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="5ff37-110">Obtient la taille d'une variable en octets.</span><span class="sxs-lookup"><span data-stu-id="5ff37-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="5ff37-111">GetSlotIndex (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ff37-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="5ff37-112">Obtient l'index d'emplacement géré d'une variable locale.</span><span class="sxs-lookup"><span data-stu-id="5ff37-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="5ff37-113">GetValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ff37-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="5ff37-114">Obtient la valeur d'une variable sous forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="5ff37-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="5ff37-115">SetValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ff37-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="5ff37-116">Affecte la valeur d'un tableau d'octets à une variable.</span><span class="sxs-lookup"><span data-stu-id="5ff37-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ff37-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ff37-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ff37-118">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5ff37-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="5ff37-119">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="5ff37-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ff37-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5ff37-120">Requirements</span></span>  
 <span data-ttu-id="5ff37-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ff37-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ff37-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ff37-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ff37-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ff37-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ff37-124">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff37-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff37-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ff37-125">See Also</span></span>  
 [<span data-ttu-id="5ff37-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5ff37-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5ff37-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="5ff37-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
