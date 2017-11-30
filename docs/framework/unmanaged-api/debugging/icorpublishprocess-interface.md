---
title: ICorPublishProcess, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cb62da277ff13bea33969bb9c728cac5d5a15554
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="2de65-102">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="2de65-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="2de65-103">Fournit des méthodes qui accèdent aux informations à afficher sur un processus.</span><span class="sxs-lookup"><span data-stu-id="2de65-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2de65-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2de65-104">Methods</span></span>  
  
|<span data-ttu-id="2de65-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2de65-105">Method</span></span>|<span data-ttu-id="2de65-106">Description</span><span class="sxs-lookup"><span data-stu-id="2de65-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2de65-107">EnumAppDomains (méthode)</span><span class="sxs-lookup"><span data-stu-id="2de65-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="2de65-108">Obtient un [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance qui contient les domaines d’application dans le processus référencé par ce `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="2de65-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="2de65-109">GetDisplayName (méthode)</span><span class="sxs-lookup"><span data-stu-id="2de65-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="2de65-110">Obtient le chemin d’accès complet du fichier exécutable pour le processus référencé par ce `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="2de65-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="2de65-111">GetProcessID (méthode)</span><span class="sxs-lookup"><span data-stu-id="2de65-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="2de65-112">Obtient l’identificateur de système d’exploitation pour le processus référencé par ce `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="2de65-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="2de65-113">IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="2de65-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="2de65-114">Obtient une valeur qui indique si le processus référencé par ce `ICorPublishProcess` est connu pour être en cours d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="2de65-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2de65-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2de65-115">Requirements</span></span>  
 <span data-ttu-id="2de65-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2de65-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2de65-117">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2de65-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2de65-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2de65-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2de65-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2de65-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de65-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2de65-120">See Also</span></span>  
 [<span data-ttu-id="2de65-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2de65-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2de65-122">CorpubPublish (coclasse)</span><span class="sxs-lookup"><span data-stu-id="2de65-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
