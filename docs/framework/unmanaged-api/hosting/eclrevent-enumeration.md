---
title: "EClrEvent, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrEvent
helpviewer_keywords: EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0585cea00865f4798c57ef5276076c2b0a5ff284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="bb3f7-102">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="bb3f7-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="bb3f7-103">Décrit les événements du common language runtime (CLR) pour laquelle l’hôte peut enregistrer des rappels.</span><span class="sxs-lookup"><span data-stu-id="bb3f7-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb3f7-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="bb3f7-105">Membres</span><span class="sxs-lookup"><span data-stu-id="bb3f7-105">Members</span></span>  
  
|<span data-ttu-id="bb3f7-106">Membre</span><span class="sxs-lookup"><span data-stu-id="bb3f7-106">Member</span></span>|<span data-ttu-id="bb3f7-107">Description</span><span class="sxs-lookup"><span data-stu-id="bb3f7-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="bb3f7-108">Spécifie une erreur irrécupérable de CLR.</span><span class="sxs-lookup"><span data-stu-id="bb3f7-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="bb3f7-109">Spécifie le déchargement d’un particulier <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="bb3f7-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="bb3f7-110">Spécifie qu’un message d’Assistant Débogage managé (MDA) a été généré.</span><span class="sxs-lookup"><span data-stu-id="bb3f7-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="bb3f7-111">Spécifie qu’une erreur de dépassement de capacité de pile s’est produite.</span><span class="sxs-lookup"><span data-stu-id="bb3f7-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb3f7-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb3f7-112">Remarks</span></span>  
 <span data-ttu-id="bb3f7-113">L’hôte peut enregistrer des rappels pour l’un des types d’événements décrits par `EClrEvent` en appelant des méthodes de la [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="bb3f7-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="bb3f7-114">L’hôte obtient un pointeur vers cette interface en appelant le [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="bb3f7-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="bb3f7-115">Le `Event_CLRDisabled` et `Event_DomainUnload` peuvent être déclenchés plusieurs fois et à partir de threads différents pour signaler le déchargement ou la désactivation du CLR.</span><span class="sxs-lookup"><span data-stu-id="bb3f7-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="bb3f7-116">Le `Event_MDAFired` événement déclenche la création d’un [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance qui contient les détails du message d’Assistant Débogage MANAGÉ.</span><span class="sxs-lookup"><span data-stu-id="bb3f7-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="bb3f7-117">Pour plus d’informations sur les Assistants Débogage managé, consultez [diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="bb3f7-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb3f7-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bb3f7-118">Requirements</span></span>  
 <span data-ttu-id="bb3f7-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb3f7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb3f7-120">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb3f7-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb3f7-121">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb3f7-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb3f7-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3f7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3f7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb3f7-123">See Also</span></span>  
 [<span data-ttu-id="bb3f7-124">IActionOnCLREvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="bb3f7-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="bb3f7-125">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="bb3f7-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="bb3f7-126">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="bb3f7-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
