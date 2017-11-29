---
title: invalidFunctionPointerInDelegate (MDA)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e9fd1faacc7be5b95e2bab0d8fdbee105e35498
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="5bfc8-102">invalidFunctionPointerInDelegate (MDA)</span><span class="sxs-lookup"><span data-stu-id="5bfc8-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="5bfc8-103">L'Assistant Débogage managé `invalidFunctionPointerInDelegate` est activé quand un pointeur de fonction non valide est transmis pour créer un délégué sur un pointeur de fonction natif.</span><span class="sxs-lookup"><span data-stu-id="5bfc8-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5bfc8-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="5bfc8-104">Symptoms</span></span>  
 <span data-ttu-id="5bfc8-105">Violations d'accès ou endommagement de mémoire inattendu pendant l'utilisation d'un délégué sur un pointeur de fonction.</span><span class="sxs-lookup"><span data-stu-id="5bfc8-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5bfc8-106">Cause</span><span class="sxs-lookup"><span data-stu-id="5bfc8-106">Cause</span></span>  
 <span data-ttu-id="5bfc8-107">Un pointeur de fonction non valide a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="5bfc8-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5bfc8-108">Solution</span><span class="sxs-lookup"><span data-stu-id="5bfc8-108">Resolution</span></span>  
 <span data-ttu-id="5bfc8-109">Spécifiez un pointeur de fonction valide.</span><span class="sxs-lookup"><span data-stu-id="5bfc8-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5bfc8-110">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="5bfc8-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="5bfc8-111">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="5bfc8-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5bfc8-112">Sortie</span><span class="sxs-lookup"><span data-stu-id="5bfc8-112">Output</span></span>  
 <span data-ttu-id="5bfc8-113">Pointeur de fonction non valide.</span><span class="sxs-lookup"><span data-stu-id="5bfc8-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5bfc8-114">Configuration</span><span class="sxs-lookup"><span data-stu-id="5bfc8-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bfc8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bfc8-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="5bfc8-116">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="5bfc8-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="5bfc8-117">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="5bfc8-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
