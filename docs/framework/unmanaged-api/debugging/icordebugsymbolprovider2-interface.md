---
title: ICorDebugSymbolProvider2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ff0446ba8646620cb7322f74a81769e41f35b0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="03cf2-102">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="03cf2-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="03cf2-103">Étend logiquement le [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface pour récupérer des informations sur les symboles de débogage supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="03cf2-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03cf2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="03cf2-104">Methods</span></span>  
  
|<span data-ttu-id="03cf2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="03cf2-105">Method</span></span>|<span data-ttu-id="03cf2-106">Description</span><span class="sxs-lookup"><span data-stu-id="03cf2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03cf2-107">GetFrameProps (méthode)</span><span class="sxs-lookup"><span data-stu-id="03cf2-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="03cf2-108">Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.</span><span class="sxs-lookup"><span data-stu-id="03cf2-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="03cf2-109">GetGenericDictionaryInfo (méthode)</span><span class="sxs-lookup"><span data-stu-id="03cf2-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="03cf2-110">Récupère un mappage de dictionnaire générique.</span><span class="sxs-lookup"><span data-stu-id="03cf2-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03cf2-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="03cf2-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03cf2-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="03cf2-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="03cf2-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="03cf2-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03cf2-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="03cf2-114">Requirements</span></span>  
 <span data-ttu-id="03cf2-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03cf2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03cf2-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03cf2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03cf2-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03cf2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03cf2-118">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03cf2-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03cf2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03cf2-119">See Also</span></span>  
 [<span data-ttu-id="03cf2-120">Icordebugsymbolprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="03cf2-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="03cf2-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="03cf2-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="03cf2-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="03cf2-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
