---
title: notMarshalable (MDA)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5de75130acab30c4f73522728c00b69c1c3e8d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="3bf47-102">notMarshalable (MDA)</span><span class="sxs-lookup"><span data-stu-id="3bf47-102">notMarshalable MDA</span></span>
<span data-ttu-id="3bf47-103">L'Assistant Débogage managé (MDA) `notMarshalable` est activé lorsque le Common Language Runtime (CLR) rencontre un pointeur d'interface COM sans proxy/stub inscrit valide ou une implémentation d'interface `IMarshal` incorrecte lors d'une tentative de marshaling de l'interface entre plusieurs contextes.</span><span class="sxs-lookup"><span data-stu-id="3bf47-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3bf47-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="3bf47-104">Symptoms</span></span>  
 <span data-ttu-id="3bf47-105">Les appels ne sont pas traités ou ils se produisent dans le contexte incorrect pour les pointeurs d'interface COM.</span><span class="sxs-lookup"><span data-stu-id="3bf47-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3bf47-106">Cause</span><span class="sxs-lookup"><span data-stu-id="3bf47-106">Cause</span></span>  
 <span data-ttu-id="3bf47-107">Absence de proxy/stub inscrit valide ou présence d'une interface `IMarshal` incorrecte lors d'une tentative de marshaling de l'interface entre plusieurs contextes.</span><span class="sxs-lookup"><span data-stu-id="3bf47-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3bf47-108">Résolution</span><span class="sxs-lookup"><span data-stu-id="3bf47-108">Resolution</span></span>  
 <span data-ttu-id="3bf47-109">Assurez-vous que vous avez un stub/proxy inscrit et que l'implémentation de `IMarshal` est correcte.</span><span class="sxs-lookup"><span data-stu-id="3bf47-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3bf47-110">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="3bf47-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="3bf47-111">Cet Assistant Débogage managé n'a aucun effet sur le runtime.</span><span class="sxs-lookup"><span data-stu-id="3bf47-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3bf47-112">Sortie</span><span class="sxs-lookup"><span data-stu-id="3bf47-112">Output</span></span>  
 <span data-ttu-id="3bf47-113">Message décrivant le problème.</span><span class="sxs-lookup"><span data-stu-id="3bf47-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3bf47-114">Configuration</span><span class="sxs-lookup"><span data-stu-id="3bf47-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bf47-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bf47-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="3bf47-116">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="3bf47-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="3bf47-117">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="3bf47-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
