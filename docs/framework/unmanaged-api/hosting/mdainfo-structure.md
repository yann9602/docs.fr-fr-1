---
title: MDAInfo, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MDAInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: MDAInfo
helpviewer_keywords: MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d303bcbee0b0c769fe2bc45663356b759fc91669
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mdainfo-structure"></a><span data-ttu-id="a9603-102">MDAInfo, structure</span><span class="sxs-lookup"><span data-stu-id="a9603-102">MDAInfo Structure</span></span>
<span data-ttu-id="a9603-103">Fournit des détails sur la `Event_MDAFired` événement qui déclenche la création d’un assistant débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="a9603-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9603-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9603-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="a9603-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a9603-105">Members</span></span>  
  
|<span data-ttu-id="a9603-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a9603-106">Member</span></span>|<span data-ttu-id="a9603-107">Description</span><span class="sxs-lookup"><span data-stu-id="a9603-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="a9603-108">Le titre de l’Assistant Débogage MANAGÉ actuel.</span><span class="sxs-lookup"><span data-stu-id="a9603-108">The title of the current MDA.</span></span> <span data-ttu-id="a9603-109">Le titre décrit le genre d’échec qui a déclenché la `Event_MDAFired` événement.</span><span class="sxs-lookup"><span data-stu-id="a9603-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="a9603-110">Le message de sortie fourni par l’Assistant Débogage MANAGÉ actuel.</span><span class="sxs-lookup"><span data-stu-id="a9603-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9603-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="a9603-111">Remarks</span></span>  
 <span data-ttu-id="a9603-112">Assistants de débogage managés (MDA) sont outils de débogage qui fonctionnent conjointement avec le common language runtime (CLR) pour effectuer des tâches telles que l’identification des conditions non valides dans le moteur d’exécution ou le vidage des informations supplémentaires sur l’état de la moteur.</span><span class="sxs-lookup"><span data-stu-id="a9603-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="a9603-113">MDA génèrent des messages XML sur les événements qui sont difficiles à intercepter.</span><span class="sxs-lookup"><span data-stu-id="a9603-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="a9603-114">Ils sont particulièrement utiles pour déboguer des transitions entre code managé et non managé.</span><span class="sxs-lookup"><span data-stu-id="a9603-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="a9603-115">Le runtime effectue les étapes suivantes lorsqu’un événement qui déclenche la création d’un Assistant Débogage MANAGÉ est déclenché :</span><span class="sxs-lookup"><span data-stu-id="a9603-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="a9603-116">Si l’hôte n’a pas inscrit un [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance en appelant [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) recevoir les notifications d’un `Event_MDAFired` événement, le runtime continue avec son comportement par défaut, non hébergé.</span><span class="sxs-lookup"><span data-stu-id="a9603-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="a9603-117">Si l’ordinateur hôte a inscrit un gestionnaire pour cet événement, le runtime vérifie si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="a9603-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="a9603-118">S’il s’agit, le runtime arrête le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a9603-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="a9603-119">Lorsque le débogueur continue, il appelle l’hôte.</span><span class="sxs-lookup"><span data-stu-id="a9603-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="a9603-120">Si aucun débogueur n’est attaché, le runtime appelle `IActionOnCLREvent::OnEvent` et passe un pointeur vers un `MDAInfo` l’instance comme le `data` paramètre.</span><span class="sxs-lookup"><span data-stu-id="a9603-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="a9603-121">L’hôte peut choisir d’activer les MDA et d’être averti quand un Assistant Débogage MANAGÉ est activé.</span><span class="sxs-lookup"><span data-stu-id="a9603-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="a9603-122">Cela permet de l’hôte de substituer le comportement par défaut et d’abandonner le thread managé qui a déclenché l’événement pour l’empêcher d’endommager l’état du processus.</span><span class="sxs-lookup"><span data-stu-id="a9603-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="a9603-123">Pour plus d’informations sur l’utilisation des Assistants Débogage managé, consultez [diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="a9603-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9603-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a9603-124">Requirements</span></span>  
 <span data-ttu-id="a9603-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9603-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9603-126">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="a9603-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a9603-127">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9603-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9603-128">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9603-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9603-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9603-129">See Also</span></span>  
 [<span data-ttu-id="a9603-130">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="a9603-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="a9603-131">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="a9603-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
