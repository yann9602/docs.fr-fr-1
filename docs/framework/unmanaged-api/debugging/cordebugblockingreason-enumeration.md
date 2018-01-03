---
title: "CorDebugBlockingReason, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingReason
helpviewer_keywords: CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84c09de4e0ce6e436c2c814c4cd9990db012d422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="b3bbb-102">CorDebugBlockingReason, énumération</span><span class="sxs-lookup"><span data-stu-id="b3bbb-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="b3bbb-103">Spécifie les raisons pour lesquelles un thread peut être bloqué sur un objet donné.</span><span class="sxs-lookup"><span data-stu-id="b3bbb-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3bbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3bbb-104">Syntax</span></span>  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="b3bbb-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b3bbb-105">Members</span></span>  
  
|<span data-ttu-id="b3bbb-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b3bbb-106">Member</span></span>|<span data-ttu-id="b3bbb-107">Description</span><span class="sxs-lookup"><span data-stu-id="b3bbb-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="b3bbb-108">Usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="b3bbb-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="b3bbb-109">Un thread essaie d’acquérir la section critique qui est associée avec le verrou du moniteur sur un objet.</span><span class="sxs-lookup"><span data-stu-id="b3bbb-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="b3bbb-110">En règle générale, cela se produit lorsque vous appelez une de le <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ou <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> méthodes.</span><span class="sxs-lookup"><span data-stu-id="b3bbb-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="b3bbb-111">Un thread est en attente sur l’événement qui est associé à un verrou de moniteur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="b3bbb-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="b3bbb-112">En règle générale, cela se produit lorsque vous appelez une de le <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` méthodes.</span><span class="sxs-lookup"><span data-stu-id="b3bbb-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3bbb-113">Notes</span><span class="sxs-lookup"><span data-stu-id="b3bbb-113">Remarks</span></span>  
 <span data-ttu-id="b3bbb-114">Lorsque le `BLOCKING_MONITOR_CRITICAL_SECTION` ou `BLOCKING_MONITOR_EVENT` membre est utilisé dans un [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, le `pBlockingObject` membre de la structure pointe vers une interface « ICorDebugValue » qui représente l’objet qui est en cours d’entrée .</span><span class="sxs-lookup"><span data-stu-id="b3bbb-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="b3bbb-115">Il est également garanti pour implémenter le [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="b3bbb-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3bbb-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b3bbb-116">Requirements</span></span>  
 <span data-ttu-id="b3bbb-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3bbb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3bbb-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3bbb-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3bbb-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3bbb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3bbb-120">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3bbb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bbb-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3bbb-121">See Also</span></span>  
 [<span data-ttu-id="b3bbb-122">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="b3bbb-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="b3bbb-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="b3bbb-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
