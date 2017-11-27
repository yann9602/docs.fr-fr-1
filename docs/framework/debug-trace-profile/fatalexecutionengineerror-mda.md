---
title: "Assistant Débogage managé fatalExecutionEngineError"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cda166645bad2ad7780da58c287880398605806f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="25b99-102">Assistant Débogage managé fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="25b99-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="25b99-103">L’Assistant Débogage managé `fatalExecutionEngine``Error` est activé quand une erreur irrécupérable dans le common language runtime a été détectée.</span><span class="sxs-lookup"><span data-stu-id="25b99-103">The `fatalExecutionEngine``Error` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="25b99-104">Le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="25b99-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="25b99-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="25b99-105">Symptoms</span></span>  
 <span data-ttu-id="25b99-106">Arrêt inattendu du processus.</span><span class="sxs-lookup"><span data-stu-id="25b99-106">Unexpected process termination.</span></span> <span data-ttu-id="25b99-107">D’autres symptômes ne peuvent pas être déterminés, car une défaillance du common language runtime peut se produire pour différentes raisons.</span><span class="sxs-lookup"><span data-stu-id="25b99-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="25b99-108">Cause</span><span class="sxs-lookup"><span data-stu-id="25b99-108">Cause</span></span>  
 <span data-ttu-id="25b99-109">Le common language runtime a été endommagé de façon irréversible.</span><span class="sxs-lookup"><span data-stu-id="25b99-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="25b99-110">Ceci est dû le plus souvent à une altération des données, qui peut être provoquée par un certain nombre de problèmes, comme des fonctions d’appel de code non managé incorrectement formées et au passage de données non valides au CLR.</span><span class="sxs-lookup"><span data-stu-id="25b99-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="25b99-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="25b99-111">Resolution</span></span>  
 <span data-ttu-id="25b99-112">L’activation d’Assistants Débogage managé supplémentaires peut aider à identifier le problème.</span><span class="sxs-lookup"><span data-stu-id="25b99-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="25b99-113">Les Assistants Débogage managé suivants peuvent être particulièrement utiles pour diagnostiquer le problème :</span><span class="sxs-lookup"><span data-stu-id="25b99-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="25b99-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="25b99-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="25b99-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="25b99-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="25b99-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="25b99-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="25b99-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="25b99-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="25b99-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="25b99-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="25b99-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="25b99-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="25b99-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="25b99-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="25b99-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="25b99-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="25b99-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="25b99-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="25b99-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="25b99-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="25b99-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="25b99-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="25b99-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="25b99-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="25b99-126">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="25b99-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="25b99-127">Cet Assistant Débogage managé n’a aucun effet sur le comportement du runtime.</span><span class="sxs-lookup"><span data-stu-id="25b99-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="25b99-128">Sortie</span><span class="sxs-lookup"><span data-stu-id="25b99-128">Output</span></span>  
 <span data-ttu-id="25b99-129">L’adresse de la fonction CLR qui a provoqué l’erreur irrécupérable, l’ID du thread où l’erreur s’est produite et le code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="25b99-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="25b99-130">Configuration</span><span class="sxs-lookup"><span data-stu-id="25b99-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="25b99-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25b99-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="25b99-132">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="25b99-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
