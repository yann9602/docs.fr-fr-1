---
title: "ETaskType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ETaskType
api_location: mscoree.dll
api_type: COM
f1_keywords: ETaskType
helpviewer_keywords: ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7973b8cbd49858daaf6f08d55c7d9f60f687a72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="8c505-102">ETaskType, énumération</span><span class="sxs-lookup"><span data-stu-id="8c505-102">ETaskType Enumeration</span></span>
<span data-ttu-id="8c505-103">Contient des valeurs qui indiquent le type de tâche est représentée par une [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ou [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="8c505-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c505-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c505-104">Syntax</span></span>  
  
```  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="8c505-105">Membres</span><span class="sxs-lookup"><span data-stu-id="8c505-105">Members</span></span>  
  
|<span data-ttu-id="8c505-106">Membre</span><span class="sxs-lookup"><span data-stu-id="8c505-106">Member</span></span>|<span data-ttu-id="8c505-107">Description</span><span class="sxs-lookup"><span data-stu-id="8c505-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="8c505-108">L’interface représente une tâche de déchargement du domaine application.</span><span class="sxs-lookup"><span data-stu-id="8c505-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="8c505-109">L’interface représente une tâche d’assistance du débogueur.</span><span class="sxs-lookup"><span data-stu-id="8c505-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="8c505-110">L’interface représente une tâche du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="8c505-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="8c505-111">L’interface représente une tâche de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8c505-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="8c505-112">L’interface représente une tâche du thread de grille.</span><span class="sxs-lookup"><span data-stu-id="8c505-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="8c505-113">L’interface représente une tâche du thread d’e/s ou une tâche de thread de port de fin.</span><span class="sxs-lookup"><span data-stu-id="8c505-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="8c505-114">L’interface représente une tâche du thread du minuteur.</span><span class="sxs-lookup"><span data-stu-id="8c505-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="8c505-115">L’interface représente une tâche de thread d’attente.</span><span class="sxs-lookup"><span data-stu-id="8c505-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="8c505-116">L’interface représente une tâche du thread de travail.</span><span class="sxs-lookup"><span data-stu-id="8c505-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="8c505-117">La tâche est inconnue.</span><span class="sxs-lookup"><span data-stu-id="8c505-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="8c505-118">L’interface représente une tâche utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8c505-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c505-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8c505-119">Requirements</span></span>  
 <span data-ttu-id="8c505-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c505-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c505-121">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c505-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c505-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c505-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c505-123">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c505-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c505-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c505-124">See Also</span></span>  
 [<span data-ttu-id="8c505-125">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="8c505-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
