---
title: "Assistant Débogage managé marshalCleanupError"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 641d12131f1502ce1ef00c6cf3889c803bd9fce3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="84a73-102">Assistant Débogage managé marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="84a73-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="84a73-103">L'Assistant Débogage managé `marshalCleanupError` est activé quand le Common Language Runtime (CLR) rencontre une erreur pendant une tentative de nettoyage de la mémoire et des structures temporaires utilisées pour le marshaling de types de données entre des limites de code native et managé.</span><span class="sxs-lookup"><span data-stu-id="84a73-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="84a73-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="84a73-104">Symptoms</span></span>  
 <span data-ttu-id="84a73-105">Une fuite de mémoire se produit en cas de transitions de code natif et managé, de non-restauration d'état d'exécution tel que la culture de thread ou d'erreurs de nettoyage <xref:System.Runtime.InteropServices.SafeHandle>.</span><span class="sxs-lookup"><span data-stu-id="84a73-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="84a73-106">Cause</span><span class="sxs-lookup"><span data-stu-id="84a73-106">Cause</span></span>  
 <span data-ttu-id="84a73-107">Une erreur inattendue s'est produite pendant le nettoyage des structures temporaires.</span><span class="sxs-lookup"><span data-stu-id="84a73-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="84a73-108">Solution</span><span class="sxs-lookup"><span data-stu-id="84a73-108">Resolution</span></span>  
 <span data-ttu-id="84a73-109">Examinez toutes les implémentations de marshaleur personnalisé, de finaliseur et de destructeur <xref:System.Runtime.InteropServices.SafeHandle> pour déterminer si elles contiennent des erreurs.</span><span class="sxs-lookup"><span data-stu-id="84a73-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="84a73-110">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="84a73-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="84a73-111">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="84a73-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="84a73-112">Sortie</span><span class="sxs-lookup"><span data-stu-id="84a73-112">Output</span></span>  
 <span data-ttu-id="84a73-113">Message indiquant l'opération ayant échoué pendant le nettoyage.</span><span class="sxs-lookup"><span data-stu-id="84a73-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="84a73-114">Configuration</span><span class="sxs-lookup"><span data-stu-id="84a73-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="84a73-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84a73-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="84a73-116">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="84a73-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="84a73-117">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="84a73-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
