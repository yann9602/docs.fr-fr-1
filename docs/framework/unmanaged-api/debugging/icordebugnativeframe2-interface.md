---
title: ICorDebugNativeFrame2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2
helpviewer_keywords: ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c33eaa36313f0cf6aae904761fb40bb2dbf9d753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="aa928-102">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="aa928-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="aa928-103">Fournit des méthodes qui testent les relations entre frames enfant et parent.</span><span class="sxs-lookup"><span data-stu-id="aa928-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa928-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="aa928-104">Methods</span></span>  
  
|<span data-ttu-id="aa928-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="aa928-105">Method</span></span>|<span data-ttu-id="aa928-106">Description</span><span class="sxs-lookup"><span data-stu-id="aa928-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa928-107">IsChild (méthode)</span><span class="sxs-lookup"><span data-stu-id="aa928-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="aa928-108">Détermine si le frame actuel est un frame enfant.</span><span class="sxs-lookup"><span data-stu-id="aa928-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="aa928-109">IsMatchingParentFrame (méthode)</span><span class="sxs-lookup"><span data-stu-id="aa928-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="aa928-110">Détermine si le frame spécifié est le parent de l’image actuelle.</span><span class="sxs-lookup"><span data-stu-id="aa928-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="aa928-111">GetStackParameterSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="aa928-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="aa928-112">Retourne la taille cumulée des paramètres de la pile sur x86 systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="aa928-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa928-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="aa928-113">Remarks</span></span>  
 <span data-ttu-id="aa928-114">Cette interface étend logiquement l’interface « ICorDebugNativeFrame ».</span><span class="sxs-lookup"><span data-stu-id="aa928-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa928-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="aa928-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa928-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="aa928-116">Requirements</span></span>  
 <span data-ttu-id="aa928-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa928-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa928-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa928-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa928-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa928-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa928-120">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa928-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa928-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa928-121">See Also</span></span>  
    
 [<span data-ttu-id="aa928-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="aa928-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="aa928-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="aa928-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
