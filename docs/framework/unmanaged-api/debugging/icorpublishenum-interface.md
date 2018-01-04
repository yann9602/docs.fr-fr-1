---
title: ICorPublishEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum
helpviewer_keywords: ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f09d0f80eba86d03d0db7af8fd63d2231c9a88d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="2c3d4-102">ICorPublishEnum, interface</span><span class="sxs-lookup"><span data-stu-id="2c3d4-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="2c3d4-103">Sert d’interface de base abstraite pour les énumérateurs qui sont utilisés dans la publication d’informations sur les processus et les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="2c3d4-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c3d4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2c3d4-104">Methods</span></span>  
  
|<span data-ttu-id="2c3d4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2c3d4-105">Method</span></span>|<span data-ttu-id="2c3d4-106">Description</span><span class="sxs-lookup"><span data-stu-id="2c3d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c3d4-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="2c3d4-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="2c3d4-108">Crée une copie de ce `ICorPublishEnum` objet.</span><span class="sxs-lookup"><span data-stu-id="2c3d4-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="2c3d4-109">GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="2c3d4-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="2c3d4-110">Obtient le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="2c3d4-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="2c3d4-111">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="2c3d4-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="2c3d4-112">Place le curseur au début de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="2c3d4-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="2c3d4-113">Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="2c3d4-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="2c3d4-114">Déplace le curseur vers l’avant dans l’énumération par le nombre spécifié d’éléments.</span><span class="sxs-lookup"><span data-stu-id="2c3d4-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c3d4-115">Notes</span><span class="sxs-lookup"><span data-stu-id="2c3d4-115">Remarks</span></span>  
 <span data-ttu-id="2c3d4-116">Les énumérateurs suivants dérivent `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="2c3d4-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="2c3d4-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="2c3d4-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="2c3d4-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="2c3d4-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="2c3d4-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2c3d4-119">Requirements</span></span>  
 <span data-ttu-id="2c3d4-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c3d4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3d4-121">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2c3d4-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2c3d4-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c3d4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c3d4-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3d4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3d4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c3d4-124">See Also</span></span>  
 [<span data-ttu-id="2c3d4-125">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="2c3d4-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="2c3d4-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2c3d4-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
