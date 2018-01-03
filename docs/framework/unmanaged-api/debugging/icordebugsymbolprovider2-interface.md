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
ms.workload: dotnet
ms.openlocfilehash: 7666b8d64b689d3640594f07614be97b72e85a8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="c49fc-102">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="c49fc-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="c49fc-103">Étend logiquement le [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface pour récupérer des informations sur les symboles de débogage supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c49fc-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c49fc-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c49fc-104">Methods</span></span>  
  
|<span data-ttu-id="c49fc-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="c49fc-105">Method</span></span>|<span data-ttu-id="c49fc-106">Description</span><span class="sxs-lookup"><span data-stu-id="c49fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c49fc-107">GetFrameProps, méthode</span><span class="sxs-lookup"><span data-stu-id="c49fc-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="c49fc-108">Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.</span><span class="sxs-lookup"><span data-stu-id="c49fc-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="c49fc-109">GetGenericDictionaryInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="c49fc-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="c49fc-110">Récupère un mappage de dictionnaire générique.</span><span class="sxs-lookup"><span data-stu-id="c49fc-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c49fc-111">Notes</span><span class="sxs-lookup"><span data-stu-id="c49fc-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c49fc-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c49fc-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c49fc-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="c49fc-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c49fc-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c49fc-114">Requirements</span></span>  
 <span data-ttu-id="c49fc-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c49fc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c49fc-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c49fc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c49fc-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c49fc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c49fc-118">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c49fc-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c49fc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c49fc-119">See Also</span></span>  
 [<span data-ttu-id="c49fc-120">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="c49fc-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="c49fc-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c49fc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c49fc-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="c49fc-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
