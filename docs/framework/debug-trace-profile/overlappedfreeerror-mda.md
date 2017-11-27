---
title: "Assistant Débogage managé overlappedFreeError"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 645c9f6c5a2a693fb2b88b2b2bc1c40501eecde8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="7665f-102">Assistant Débogage managé overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="7665f-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="7665f-103">L’Assistant Débogage managé `overlappedFreeError` est activé quand la méthode <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> est appelée avant la fin de l’opération avec chevauchement.</span><span class="sxs-lookup"><span data-stu-id="7665f-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7665f-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="7665f-104">Symptoms</span></span>  
 <span data-ttu-id="7665f-105">Violations d’accès ou altération du tas de la garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7665f-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7665f-106">Cause</span><span class="sxs-lookup"><span data-stu-id="7665f-106">Cause</span></span>  
 <span data-ttu-id="7665f-107">Une structure avec chevauchement a été libérée avant la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="7665f-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="7665f-108">La fonction qui utilise le pointeur avec chevauchement peut écrire dans la structure ultérieurement, une fois qu’elle a été libérée.</span><span class="sxs-lookup"><span data-stu-id="7665f-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="7665f-109">Ceci peut entraîner une altération du tas, car un autre objet devrait maintenant occuper cette région.</span><span class="sxs-lookup"><span data-stu-id="7665f-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="7665f-110">Cet Assistant Débogage managé peut ne pas représenter une erreur si l’opération avec chevauchement n’a pas démarré correctement.</span><span class="sxs-lookup"><span data-stu-id="7665f-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7665f-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="7665f-111">Resolution</span></span>  
 <span data-ttu-id="7665f-112">Vérifiez que l’opération d’E/S utilisant la structure avec chevauchement est terminée avant d’appeler la méthode <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29>.</span><span class="sxs-lookup"><span data-stu-id="7665f-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7665f-113">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="7665f-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="7665f-114">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="7665f-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7665f-115">Sortie</span><span class="sxs-lookup"><span data-stu-id="7665f-115">Output</span></span>  
 <span data-ttu-id="7665f-116">Voici un exemple de sortie pour cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="7665f-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="7665f-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="7665f-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7665f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7665f-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="7665f-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="7665f-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="7665f-120">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="7665f-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
