---
title: ICorDebugAssembly3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e581b4256da2ecc19a8b97520e0e70fef972b549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="f9d41-102">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="f9d41-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="f9d41-103">Étend logiquement l’interface ICorDebugAssembly pour prendre en charge pour les assemblys conteneurs et les assemblys.</span><span class="sxs-lookup"><span data-stu-id="f9d41-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9d41-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f9d41-104">Methods</span></span>  
  
|<span data-ttu-id="f9d41-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f9d41-105">Method</span></span>|<span data-ttu-id="f9d41-106">Description</span><span class="sxs-lookup"><span data-stu-id="f9d41-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9d41-107">EnumerateContainedAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="f9d41-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="f9d41-108">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="f9d41-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="f9d41-109">GetContainerAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="f9d41-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="f9d41-110">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="f9d41-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9d41-111">Notes</span><span class="sxs-lookup"><span data-stu-id="f9d41-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9d41-112">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f9d41-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="f9d41-113">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f9d41-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9d41-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f9d41-114">Requirements</span></span>  
 <span data-ttu-id="f9d41-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9d41-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9d41-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9d41-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9d41-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9d41-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9d41-118">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9d41-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d41-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9d41-119">See Also</span></span>  
 [<span data-ttu-id="f9d41-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f9d41-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f9d41-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="f9d41-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
