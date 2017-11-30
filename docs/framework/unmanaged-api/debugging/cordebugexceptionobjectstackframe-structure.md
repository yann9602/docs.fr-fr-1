---
title: CorDebugExceptionObjectStackFrame, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionObjectStackFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionObjectStackFrame
helpviewer_keywords: CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf166f606aa2c0e0900356395c36bd6875897e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="5a660-102">CorDebugExceptionObjectStackFrame, structure</span><span class="sxs-lookup"><span data-stu-id="5a660-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="5a660-103">Représente les informations de frame de pile provenant d'un objet Exception.</span><span class="sxs-lookup"><span data-stu-id="5a660-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a660-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a660-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="5a660-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5a660-105">Members</span></span>  
  
|<span data-ttu-id="5a660-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5a660-106">Member</span></span>|<span data-ttu-id="5a660-107">Description</span><span class="sxs-lookup"><span data-stu-id="5a660-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="5a660-108">Pointeur vers l’objet ICorDebugModule pour le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="5a660-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="5a660-109">La valeur du pointeur d’instruction (EIP/RIP) pour le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="5a660-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="5a660-110">Le jeton de méthode pour le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="5a660-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="5a660-111">Une valeur qui indique si le frame est la dernière image étrangère d’une exception.</span><span class="sxs-lookup"><span data-stu-id="5a660-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a660-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="5a660-112">Remarks</span></span>  
 <span data-ttu-id="5a660-113">L’appelant doit libérer le pointeur vers l’objet ICorDebugModule une fois qu’il n’est plus en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="5a660-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a660-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5a660-114">Requirements</span></span>  
 <span data-ttu-id="5a660-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a660-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a660-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a660-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a660-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a660-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a660-118">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a660-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a660-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a660-119">See Also</span></span>  
 [<span data-ttu-id="5a660-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="5a660-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="5a660-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="5a660-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
