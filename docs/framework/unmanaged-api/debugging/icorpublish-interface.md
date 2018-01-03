---
title: ICorPublish, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish
helpviewer_keywords: ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7769d26d65a97ea8d1b109e0098eae7e7d51ed10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublish-interface"></a><span data-ttu-id="ccb4c-102">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="ccb4c-102">ICorPublish Interface</span></span>
<span data-ttu-id="ccb4c-103">Sert d’interface générale pour la publication des informations sur les processus et des informations sur les domaines d’application dans ces processus.</span><span class="sxs-lookup"><span data-stu-id="ccb4c-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccb4c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ccb4c-104">Methods</span></span>  
  
|<span data-ttu-id="ccb4c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ccb4c-105">Method</span></span>|<span data-ttu-id="ccb4c-106">Description</span><span class="sxs-lookup"><span data-stu-id="ccb4c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccb4c-107">EnumProcesses, méthode</span><span class="sxs-lookup"><span data-stu-id="ccb4c-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="ccb4c-108">Obtient un [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance qui contient les processus managés s’exécutant sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ccb4c-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="ccb4c-109">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="ccb4c-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="ccb4c-110">Obtient un [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance qui représente le processus avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="ccb4c-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ccb4c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ccb4c-111">Requirements</span></span>  
 <span data-ttu-id="ccb4c-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccb4c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccb4c-113">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ccb4c-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ccb4c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccb4c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccb4c-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccb4c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb4c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccb4c-116">See Also</span></span>  
 [<span data-ttu-id="ccb4c-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ccb4c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ccb4c-118">CorpubPublish, coclasse</span><span class="sxs-lookup"><span data-stu-id="ccb4c-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
