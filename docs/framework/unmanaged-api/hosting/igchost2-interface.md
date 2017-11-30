---
title: IGCHost2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2
helpviewer_keywords: IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6706696e3fd5158d2b49a4d114d978a26510b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="igchost2-interface"></a><span data-ttu-id="b5bdd-102">IGCHost2, interface</span><span class="sxs-lookup"><span data-stu-id="b5bdd-102">IGCHost2 Interface</span></span>
<span data-ttu-id="b5bdd-103">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et contrôler certains aspects du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b5bdd-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5bdd-104">Pour tout nouveau développement, nous vous recommandons d’utiliser le [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) à la place de l’interface.</span><span class="sxs-lookup"><span data-stu-id="b5bdd-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5bdd-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b5bdd-105">Methods</span></span>  
  
|<span data-ttu-id="b5bdd-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="b5bdd-106">Method</span></span>|<span data-ttu-id="b5bdd-107">Description</span><span class="sxs-lookup"><span data-stu-id="b5bdd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5bdd-108">SetGCStartupLimitsEx (méthode)</span><span class="sxs-lookup"><span data-stu-id="b5bdd-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="b5bdd-109">Définit la taille du segment et la taille maximale pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="b5bdd-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="b5bdd-110">Permet la génération 0 et la taille de segment est supérieure à `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="b5bdd-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5bdd-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b5bdd-111">Requirements</span></span>  
 <span data-ttu-id="b5bdd-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5bdd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5bdd-113">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b5bdd-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b5bdd-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5bdd-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5bdd-115">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5bdd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5bdd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5bdd-116">See Also</span></span>  
 [<span data-ttu-id="b5bdd-117">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="b5bdd-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b5bdd-118">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="b5bdd-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="b5bdd-119">Corruntimehost, coclasse</span><span class="sxs-lookup"><span data-stu-id="b5bdd-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
