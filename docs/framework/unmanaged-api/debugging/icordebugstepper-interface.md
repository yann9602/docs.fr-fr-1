---
title: ICorDebugStepper Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper
helpviewer_keywords: ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83d394669270eb26b33e084b20a621e18b5b14aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepper-interface1"></a><span data-ttu-id="5a75b-102">ICorDebugStepper Interface1</span><span class="sxs-lookup"><span data-stu-id="5a75b-102">ICorDebugStepper Interface1</span></span>
<span data-ttu-id="5a75b-103">Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.</span><span class="sxs-lookup"><span data-stu-id="5a75b-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a75b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5a75b-104">Methods</span></span>  
  
|<span data-ttu-id="5a75b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5a75b-105">Method</span></span>|<span data-ttu-id="5a75b-106">Description</span><span class="sxs-lookup"><span data-stu-id="5a75b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a75b-107">Deactivate (méthode)</span><span class="sxs-lookup"><span data-stu-id="5a75b-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="5a75b-108">Cela entraîne `ICorDebugStepper` pour annuler la dernière commande reçue.</span><span class="sxs-lookup"><span data-stu-id="5a75b-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="5a75b-109">IsActive (méthode)</span><span class="sxs-lookup"><span data-stu-id="5a75b-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="5a75b-110">Obtient une valeur qui indique si cette `ICorDebugStepper` exécute actuellement une étape.</span><span class="sxs-lookup"><span data-stu-id="5a75b-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="5a75b-111">SetInterceptMask, méthode</span><span class="sxs-lookup"><span data-stu-id="5a75b-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="5a75b-112">Définit une valeur CorDebugIntercept qui spécifie les types de code qui sont en retrait dans.</span><span class="sxs-lookup"><span data-stu-id="5a75b-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="5a75b-113">SetRangeIL (méthode)</span><span class="sxs-lookup"><span data-stu-id="5a75b-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="5a75b-114">Définit une valeur qui indique si les appels à [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) valeurs d’argument par rapport à du code natif ou au code de Microsoft intermediate language (MSIL) de la méthode qui est en cours a présenté.</span><span class="sxs-lookup"><span data-stu-id="5a75b-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="5a75b-115">SetUnmappedStopMask (méthode)</span><span class="sxs-lookup"><span data-stu-id="5a75b-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="5a75b-116">Définit une valeur CorDebugUnmappedStop qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.</span><span class="sxs-lookup"><span data-stu-id="5a75b-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="5a75b-117">Step (méthode)</span><span class="sxs-lookup"><span data-stu-id="5a75b-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="5a75b-118">Cela entraîne `ICorDebugStepper` à pas son thread conteneur et éventuellement, continuez le pas à pas via des fonctions appelées dans le thread.</span><span class="sxs-lookup"><span data-stu-id="5a75b-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="5a75b-119">StepOut, méthode</span><span class="sxs-lookup"><span data-stu-id="5a75b-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="5a75b-120">Cela entraîne `ICorDebugStepper` à pas son thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.</span><span class="sxs-lookup"><span data-stu-id="5a75b-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="5a75b-121">StepRange (méthode)</span><span class="sxs-lookup"><span data-stu-id="5a75b-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="5a75b-122">Cela entraîne `ICorDebugStepper` à pas son thread conteneur et à retourner lorsqu’il atteint le code situé au-delà de la dernière des plages spécifiées.</span><span class="sxs-lookup"><span data-stu-id="5a75b-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a75b-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="5a75b-123">Remarks</span></span>  
 <span data-ttu-id="5a75b-124">Le `ICorDebugStepper` interface remplit les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a75b-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="5a75b-125">Il fait Office d’identificateur entre une commande d’étape émis et l’achèvement de cette commande.</span><span class="sxs-lookup"><span data-stu-id="5a75b-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="5a75b-126">Il fournit une interface centrale pour encapsuler le pas à pas qui peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="5a75b-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="5a75b-127">Il fournit un moyen de prématurément annuler une opération pas à pas.</span><span class="sxs-lookup"><span data-stu-id="5a75b-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="5a75b-128">Il peut y avoir plus d’une exécution pas à pas par thread.</span><span class="sxs-lookup"><span data-stu-id="5a75b-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="5a75b-129">Par exemple, un point d’arrêt peut être atteint lors de l’exécution pas à pas principal dans une fonction, et l’utilisateur peut souhaiter de démarrer une nouvelle opération pas à pas à l’intérieur de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="5a75b-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="5a75b-130">Il incombe au débogueur de déterminer comment gérer cette situation.</span><span class="sxs-lookup"><span data-stu-id="5a75b-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="5a75b-131">Le débogueur peut être amené à annuler l’opération de pas à pas d’origine ou imbriquer les deux opérations.</span><span class="sxs-lookup"><span data-stu-id="5a75b-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="5a75b-132">Le `ICorDebugStepper` interface prend en charge ces deux possibilités.</span><span class="sxs-lookup"><span data-stu-id="5a75b-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="5a75b-133">Une exécution pas à pas peut migrer entre des threads si le common language runtime (CLR) effectue un appel marshalé entre les threads.</span><span class="sxs-lookup"><span data-stu-id="5a75b-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a75b-134">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="5a75b-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a75b-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5a75b-135">Requirements</span></span>  
 <span data-ttu-id="5a75b-136">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a75b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a75b-137">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a75b-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a75b-138">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a75b-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a75b-139">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a75b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a75b-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a75b-140">See Also</span></span>  
 [<span data-ttu-id="5a75b-141">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5a75b-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
