---
title: ICorDebugMetaDataLocator, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMetaDataLocator
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMetaDataLocator
helpviewer_keywords: ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dead97961713f2d19147e242a6161aa9477905a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="681b2-102">ICorDebugMetaDataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="681b2-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="681b2-103">Fournit des informations de métadonnées au débogueur.</span><span class="sxs-lookup"><span data-stu-id="681b2-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="681b2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="681b2-104">Methods</span></span>  
  
|<span data-ttu-id="681b2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="681b2-105">Method</span></span>|<span data-ttu-id="681b2-106">Description</span><span class="sxs-lookup"><span data-stu-id="681b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="681b2-107">GetMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="681b2-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="681b2-108">Indique au débogueur de retourner le chemin d’accès complet à un module dont les métadonnées sont nécessaires pour effectuer une opération demandée par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="681b2-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="681b2-109">Notes</span><span class="sxs-lookup"><span data-stu-id="681b2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="681b2-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="681b2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="681b2-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="681b2-111">Requirements</span></span>  
 <span data-ttu-id="681b2-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="681b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="681b2-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="681b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="681b2-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="681b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="681b2-115">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="681b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681b2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="681b2-116">See Also</span></span>  
 [<span data-ttu-id="681b2-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="681b2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="681b2-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="681b2-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
