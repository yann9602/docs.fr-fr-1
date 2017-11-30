---
title: ICorDebugDataTarget2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 034e7d46c1b38aecdab18ea3a7d3b149b3d59369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="24267-102">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="24267-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="24267-103">Étend logiquement le [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span><span class="sxs-lookup"><span data-stu-id="24267-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24267-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="24267-104">Methods</span></span>  
  
|<span data-ttu-id="24267-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="24267-105">Method</span></span>|<span data-ttu-id="24267-106">Description</span><span class="sxs-lookup"><span data-stu-id="24267-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24267-107">Createvirtualunwinder, méthode</span><span class="sxs-lookup"><span data-stu-id="24267-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="24267-108">Crée un dérouleur de pile qui commence le déroulement à partir d'un contexte initial (qui n'est pas forcément la feuille d'un thread).</span><span class="sxs-lookup"><span data-stu-id="24267-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="24267-109">Enumeratethreadids, méthode</span><span class="sxs-lookup"><span data-stu-id="24267-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="24267-110">Retourne une liste des ID de threads actifs.</span><span class="sxs-lookup"><span data-stu-id="24267-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="24267-111">Getimagefrompointer, méthode</span><span class="sxs-lookup"><span data-stu-id="24267-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="24267-112">Retourne l'adresse de base et la taille d'un module à partir d'une adresse présente dans ce module.</span><span class="sxs-lookup"><span data-stu-id="24267-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="24267-113">Getimagelocation, méthode</span><span class="sxs-lookup"><span data-stu-id="24267-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="24267-114">Retourne le chemin d’accès d’un module à partir de l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="24267-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="24267-115">Getsymbolproviderforimage, méthode</span><span class="sxs-lookup"><span data-stu-id="24267-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="24267-116">Retourne le fournisseur de symboles d'un module à partir de l'adresse de base de ce module.</span><span class="sxs-lookup"><span data-stu-id="24267-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24267-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="24267-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24267-118">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="24267-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="24267-119">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="24267-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24267-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="24267-120">Requirements</span></span>  
 <span data-ttu-id="24267-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24267-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24267-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24267-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24267-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24267-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24267-124">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24267-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24267-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24267-125">See Also</span></span>  
 [<span data-ttu-id="24267-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="24267-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="24267-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="24267-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
