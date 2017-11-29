---
title: ICorDebugModuleBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleBreakpoint
helpviewer_keywords: ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e3937c6c0baef4cc927b5c5d789826c70beebf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="e7a59-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="e7a59-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="e7a59-103">Fournit l’accès à des modules spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e7a59-103">Provides access to specific modules.</span></span> <span data-ttu-id="e7a59-104">Cette interface est une sous-classe de l’interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="e7a59-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7a59-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e7a59-105">Methods</span></span>  
  
|<span data-ttu-id="e7a59-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e7a59-106">Method</span></span>|<span data-ttu-id="e7a59-107">Description</span><span class="sxs-lookup"><span data-stu-id="e7a59-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7a59-108">GetModule (méthode)</span><span class="sxs-lookup"><span data-stu-id="e7a59-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="e7a59-109">Obtient un pointeur d’interface vers un ICorDebugModule qui référence le module où ce point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="e7a59-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7a59-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="e7a59-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7a59-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="e7a59-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a59-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e7a59-112">Requirements</span></span>  
 <span data-ttu-id="e7a59-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7a59-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a59-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7a59-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7a59-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7a59-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7a59-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a59-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a59-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7a59-117">See Also</span></span>  
 [<span data-ttu-id="e7a59-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e7a59-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
