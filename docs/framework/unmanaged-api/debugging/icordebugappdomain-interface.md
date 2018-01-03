---
title: ICorDebugAppDomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain
helpviewer_keywords: ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aab18cb1d29931a58e64561f23d91ee4eb3a4278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="08b55-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="08b55-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="08b55-103">Fournit des méthodes pour le débogage de domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="08b55-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="08b55-104">Cette interface est une sous-classe de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="08b55-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08b55-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="08b55-105">Methods</span></span>  
  
|<span data-ttu-id="08b55-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-106">Method</span></span>|<span data-ttu-id="08b55-107">Description</span><span class="sxs-lookup"><span data-stu-id="08b55-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08b55-108">Attach, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="08b55-109">Attache le débogueur au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="08b55-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="08b55-110">EnumerateAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="08b55-111">Obtient un énumérateur pour les assemblys dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="08b55-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="08b55-112">EnumerateBreakpoints, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="08b55-113">Obtient un énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="08b55-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="08b55-114">EnumerateSteppers, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="08b55-115">Obtient un énumérateur pour toutes les exécutions de pas à pas actives dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="08b55-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="08b55-116">GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="08b55-117">Obtient l’ID unique du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="08b55-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="08b55-118">GetModuleFromMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="08b55-119">Obtient l’objet ICorDebugModule avec l’interface de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="08b55-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="08b55-120">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="08b55-121">Obtient le nom du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="08b55-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="08b55-122">GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="08b55-123">Obtient un pointeur d’interface vers le domaine d’application du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="08b55-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="08b55-124">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="08b55-125">Obtient le processus qui contient le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="08b55-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="08b55-126">IsAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="08b55-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="08b55-127">Détermine si le débogueur est attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="08b55-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08b55-128">Notes</span><span class="sxs-lookup"><span data-stu-id="08b55-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08b55-129">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="08b55-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08b55-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08b55-130">Requirements</span></span>  
 <span data-ttu-id="08b55-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08b55-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08b55-132">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08b55-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08b55-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08b55-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08b55-134">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08b55-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b55-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08b55-135">See Also</span></span>  
 [<span data-ttu-id="08b55-136">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="08b55-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
