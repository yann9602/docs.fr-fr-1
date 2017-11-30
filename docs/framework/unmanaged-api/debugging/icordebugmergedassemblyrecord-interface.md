---
title: ICorDebugMergedAssemblyRecord, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 301d7d3d20b78e833101de1df8fd5c271a757144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="8ed89-102">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="8ed89-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="8ed89-103">Fournit des informations sur un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="8ed89-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ed89-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8ed89-104">Methods</span></span>  
  
|<span data-ttu-id="8ed89-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="8ed89-105">Method</span></span>|<span data-ttu-id="8ed89-106">Description</span><span class="sxs-lookup"><span data-stu-id="8ed89-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ed89-107">GetCulture (méthode)</span><span class="sxs-lookup"><span data-stu-id="8ed89-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="8ed89-108">Obtient la chaîne de nom de culture de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8ed89-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="8ed89-109">GetIndex (méthode)</span><span class="sxs-lookup"><span data-stu-id="8ed89-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="8ed89-110">Obtient l'index de préfixe de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8ed89-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="8ed89-111">GetPublicKey (méthode)</span><span class="sxs-lookup"><span data-stu-id="8ed89-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="8ed89-112">Obtient la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8ed89-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="8ed89-113">GetPublicKeyToken, méthode</span><span class="sxs-lookup"><span data-stu-id="8ed89-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="8ed89-114">Obtient le jeton de clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8ed89-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="8ed89-115">GetSimpleName (méthode)</span><span class="sxs-lookup"><span data-stu-id="8ed89-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="8ed89-116">Obtient le nom simple de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8ed89-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="8ed89-117">GetVersion (méthode)</span><span class="sxs-lookup"><span data-stu-id="8ed89-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="8ed89-118">Obtient les informations de version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8ed89-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ed89-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ed89-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ed89-120">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8ed89-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8ed89-121">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="8ed89-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ed89-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ed89-122">Requirements</span></span>  
 <span data-ttu-id="8ed89-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ed89-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ed89-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ed89-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ed89-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ed89-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ed89-126">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ed89-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed89-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ed89-127">See Also</span></span>  
 [<span data-ttu-id="8ed89-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8ed89-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8ed89-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="8ed89-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
