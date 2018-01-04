---
title: ICorPublishProcessEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcessEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcessEnum
helpviewer_keywords: ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3598af7dcdfa106b50e884c0f9d3752a595da89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="05c11-102">ICorPublishProcessEnum, interface</span><span class="sxs-lookup"><span data-stu-id="05c11-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="05c11-103">Une sous-classe de la [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface qui fournit des méthodes pour parcourir une collection de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objets.</span><span class="sxs-lookup"><span data-stu-id="05c11-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05c11-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="05c11-104">Methods</span></span>  
  
|<span data-ttu-id="05c11-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="05c11-105">Method</span></span>|<span data-ttu-id="05c11-106">Description</span><span class="sxs-lookup"><span data-stu-id="05c11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05c11-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="05c11-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="05c11-108">Obtient le nombre spécifié de `ICorPublishProcess` les instances de la collection, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="05c11-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05c11-109">Notes</span><span class="sxs-lookup"><span data-stu-id="05c11-109">Remarks</span></span>  
 <span data-ttu-id="05c11-110">Le `ICorPublishProcessEnum` interface implémente les méthodes de l’interface abstraite [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="05c11-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="05c11-111">Un `ICorPublishProcessEnum` instance est créée par le [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="05c11-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="05c11-112">Le parcours de la collection de `ICorPublishProcess` objets est basée sur les critères de filtre fournis au moment où le `ICorPublishProcessEnum` instance a été créée.</span><span class="sxs-lookup"><span data-stu-id="05c11-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05c11-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05c11-113">Requirements</span></span>  
 <span data-ttu-id="05c11-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05c11-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05c11-115">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="05c11-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="05c11-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05c11-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05c11-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05c11-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c11-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05c11-118">See Also</span></span>  
 [<span data-ttu-id="05c11-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="05c11-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="05c11-120">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="05c11-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
