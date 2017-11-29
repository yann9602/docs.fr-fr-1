---
title: "IHostTask::Start, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1a289099245228b8806639cb98f579bc56317b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="cae6f-102">IHostTask::Start, méthode</span><span class="sxs-lookup"><span data-stu-id="cae6f-102">IHostTask::Start Method</span></span>
<span data-ttu-id="cae6f-103">Demande que l’hôte déplace la tâche représentée par le [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance à partir d’une suspension à un état actif, dans lequel le code peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="cae6f-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cae6f-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cae6f-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cae6f-105">Return Value</span></span>  
  
|<span data-ttu-id="cae6f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cae6f-106">HRESULT</span></span>|<span data-ttu-id="cae6f-107">Description</span><span class="sxs-lookup"><span data-stu-id="cae6f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cae6f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="cae6f-108">S_OK</span></span>|<span data-ttu-id="cae6f-109">Start retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cae6f-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="cae6f-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cae6f-110">E_FAIL</span></span>|<span data-ttu-id="cae6f-111">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cae6f-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cae6f-112">Lorsqu’une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cae6f-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="cae6f-113">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cae6f-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cae6f-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="cae6f-114">Remarks</span></span>  
 <span data-ttu-id="cae6f-115">`Start`Retourne toujours une valeur HRESULT de S_OK, sauf dans les cas où une panne s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cae6f-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cae6f-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cae6f-116">Requirements</span></span>  
 <span data-ttu-id="cae6f-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cae6f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cae6f-118">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cae6f-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cae6f-119">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cae6f-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cae6f-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cae6f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae6f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cae6f-121">See Also</span></span>  
 [<span data-ttu-id="cae6f-122">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="cae6f-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="cae6f-123">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cae6f-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cae6f-124">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="cae6f-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="cae6f-125">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cae6f-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
