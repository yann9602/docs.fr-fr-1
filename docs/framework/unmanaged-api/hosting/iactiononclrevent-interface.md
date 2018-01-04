---
title: IActionOnCLREvent, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent
helpviewer_keywords: IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b51784f07a90faa9eeb29c18a784d4fbc2c4654
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="543b2-102">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="543b2-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="543b2-103">Fournit la [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) (méthode), qui exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="543b2-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="543b2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="543b2-104">Methods</span></span>  
  
|<span data-ttu-id="543b2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="543b2-105">Method</span></span>|<span data-ttu-id="543b2-106">Description</span><span class="sxs-lookup"><span data-stu-id="543b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="543b2-107">OnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="543b2-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="543b2-108">Exécute un rappel pour un événement enregistré.</span><span class="sxs-lookup"><span data-stu-id="543b2-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="543b2-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="543b2-109">Requirements</span></span>  
 <span data-ttu-id="543b2-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="543b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="543b2-111">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="543b2-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="543b2-112">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="543b2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="543b2-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="543b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543b2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="543b2-114">See Also</span></span>  
 [<span data-ttu-id="543b2-115">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="543b2-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="543b2-116">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="543b2-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="543b2-117">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="543b2-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="543b2-118">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="543b2-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
