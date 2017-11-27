---
title: IApartmentCallback, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IApartmentCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: IApartmentCallback
helpviewer_keywords: IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d2f2ea73da2273ff6f0abb725ec3e3fb8ca79ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="fca4f-102">IApartmentCallback, interface</span><span class="sxs-lookup"><span data-stu-id="fca4f-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="fca4f-103">Fournit des méthodes pour effectuer des rappels dans un thread cloisonné.</span><span class="sxs-lookup"><span data-stu-id="fca4f-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="fca4f-104">Un *cloisonnement* est un conteneur logique dans un processus pour les objets qui partagent les mêmes exigences d’accès de thread.</span><span class="sxs-lookup"><span data-stu-id="fca4f-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fca4f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fca4f-105">Methods</span></span>  
  
|<span data-ttu-id="fca4f-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="fca4f-106">Method</span></span>|<span data-ttu-id="fca4f-107">Description</span><span class="sxs-lookup"><span data-stu-id="fca4f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fca4f-108">DoCallback (méthode)</span><span class="sxs-lookup"><span data-stu-id="fca4f-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="fca4f-109">Exécute la fonction spécifiée dans un thread cloisonné.</span><span class="sxs-lookup"><span data-stu-id="fca4f-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fca4f-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fca4f-110">Requirements</span></span>  
 <span data-ttu-id="fca4f-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fca4f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fca4f-112">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fca4f-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fca4f-113">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fca4f-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fca4f-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fca4f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca4f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fca4f-115">See Also</span></span>  
 [<span data-ttu-id="fca4f-116">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="fca4f-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
