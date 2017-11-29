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
ms.openlocfilehash: b9ed476746e627be987e6307bd367f0d16374de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="40737-102">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="40737-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="40737-103">Étend logiquement l’interface ICorDebugAssembly pour prendre en charge pour les assemblys conteneurs et les assemblys.</span><span class="sxs-lookup"><span data-stu-id="40737-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40737-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="40737-104">Methods</span></span>  
  
|<span data-ttu-id="40737-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="40737-105">Method</span></span>|<span data-ttu-id="40737-106">Description</span><span class="sxs-lookup"><span data-stu-id="40737-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40737-107">Enumeratecontainedassemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="40737-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="40737-108">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="40737-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="40737-109">Getcontainerassembly, méthode</span><span class="sxs-lookup"><span data-stu-id="40737-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="40737-110">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="40737-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40737-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="40737-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40737-112">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="40737-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="40737-113">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="40737-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40737-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="40737-114">Requirements</span></span>  
 <span data-ttu-id="40737-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40737-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40737-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40737-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40737-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40737-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40737-118">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40737-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40737-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40737-119">See Also</span></span>  
 [<span data-ttu-id="40737-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="40737-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="40737-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="40737-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
