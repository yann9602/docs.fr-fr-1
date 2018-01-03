---
title: "Assistant Débogage managé illegalPrepareConstrainedRegion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b739cb76827a12a9928e0268e5e2cb8be686479
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="9acca-102">Assistant Débogage managé illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="9acca-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="9acca-103">L’Assistant Débogage managé `illegalPrepareConstrainedRegion` est activé quand un appel de méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> ne précède pas immédiatement l’instruction `try` du gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="9acca-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="9acca-104">Cette restriction étant au niveau MSIL, il est permis d’avoir une source générant du non-code entre l’appel et `try`, telle que les commentaires.</span><span class="sxs-lookup"><span data-stu-id="9acca-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9acca-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="9acca-105">Symptoms</span></span>  
 <span data-ttu-id="9acca-106">Une région d’exécution limitée n’est jamais traitée comme telle, mais comme un bloc de gestion des exceptions simple (`finally` ou `catch`).</span><span class="sxs-lookup"><span data-stu-id="9acca-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="9acca-107">Par conséquent, la région ne s’exécute pas en cas de mémoire insuffisante ou d’interruption de thread.</span><span class="sxs-lookup"><span data-stu-id="9acca-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9acca-108">Cause</span><span class="sxs-lookup"><span data-stu-id="9acca-108">Cause</span></span>  
 <span data-ttu-id="9acca-109">Le modèle de préparation pour une région d’exécution limitée n’est pas suivi correctement.</span><span class="sxs-lookup"><span data-stu-id="9acca-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="9acca-110">Il s’agit d’un événement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9acca-110">This is an error event.</span></span> <span data-ttu-id="9acca-111">Le <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> appel de méthode utilisé pour marquer des gestionnaires d’exceptions comme introduisant une CER dans leurs `catch` / `finally` / `fault` / `filter` blocs doivent être utilisés qu’immédiatement avant le `try` instruction.</span><span class="sxs-lookup"><span data-stu-id="9acca-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9acca-112">Résolution</span><span class="sxs-lookup"><span data-stu-id="9acca-112">Resolution</span></span>  
 <span data-ttu-id="9acca-113">Vérifiez que l’appel à <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> se produit immédiatement avant l’instruction `try`.</span><span class="sxs-lookup"><span data-stu-id="9acca-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9acca-114">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="9acca-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="9acca-115">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="9acca-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9acca-116">Sortie</span><span class="sxs-lookup"><span data-stu-id="9acca-116">Output</span></span>  
 <span data-ttu-id="9acca-117">L’Assistant Débogage managé affiche le nom de la méthode qui appelle la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, l’offset MSIL et un message indiquant que l’appel ne précède pas immédiatement le début du bloc try.</span><span class="sxs-lookup"><span data-stu-id="9acca-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9acca-118">Configuration</span><span class="sxs-lookup"><span data-stu-id="9acca-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9acca-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="9acca-119">Example</span></span>  
 <span data-ttu-id="9acca-120">L’exemple de code suivant illustre le modèle qui provoque l’activation de cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="9acca-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```  
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9acca-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9acca-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [<span data-ttu-id="9acca-122">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="9acca-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="9acca-123">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="9acca-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
