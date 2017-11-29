---
title: "CorDebugExceptionUnwindCallbackType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionUnwindCallbackType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionUnwindCallbackType
helpviewer_keywords: CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8528b2839c4972dd44f03db5f331acb672cfeb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="d1ed1-102">CorDebugExceptionUnwindCallbackType, énumération</span><span class="sxs-lookup"><span data-stu-id="d1ed1-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="d1ed1-103">Indique l'événement qui est signalé par le rappel lors de la phase de déroulement.</span><span class="sxs-lookup"><span data-stu-id="d1ed1-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ed1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1ed1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="d1ed1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d1ed1-105">Members</span></span>  
  
|<span data-ttu-id="d1ed1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d1ed1-106">Member</span></span>|<span data-ttu-id="d1ed1-107">Description</span><span class="sxs-lookup"><span data-stu-id="d1ed1-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="d1ed1-108">Début du processus de déroulement.</span><span class="sxs-lookup"><span data-stu-id="d1ed1-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="d1ed1-109">L’exception a été interceptée.</span><span class="sxs-lookup"><span data-stu-id="d1ed1-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1ed1-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d1ed1-110">Requirements</span></span>  
 <span data-ttu-id="d1ed1-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1ed1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1ed1-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1ed1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1ed1-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1ed1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1ed1-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1ed1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ed1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1ed1-115">See Also</span></span>  
 [<span data-ttu-id="d1ed1-116">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="d1ed1-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
