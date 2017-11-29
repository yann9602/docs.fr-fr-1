---
title: "Assistant Débogage managé failedQI"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87fe67e1e64d69912095e1d9587d277805a3eb80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="failedqi-mda"></a><span data-ttu-id="c45f9-102">Assistant Débogage managé failedQI</span><span class="sxs-lookup"><span data-stu-id="c45f9-102">failedQI MDA</span></span>
<span data-ttu-id="c45f9-103">L'Assistant Débogage managé (MDA) `failedQI` est activé quand le runtime appelle `QueryInterface` sur un pointeur d'interface COM au nom d'un wrapper RCW et que l'appel à `QueryInterface` échoue.</span><span class="sxs-lookup"><span data-stu-id="c45f9-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c45f9-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="c45f9-104">Symptoms</span></span>  
 <span data-ttu-id="c45f9-105">Un cast sur un RCW échoue ou un appel à COM à partir d'un RCW échoue de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="c45f9-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c45f9-106">Cause</span><span class="sxs-lookup"><span data-stu-id="c45f9-106">Cause</span></span>  
  
-   <span data-ttu-id="c45f9-107">L'appel est effectué à partir du contexte incorrect.</span><span class="sxs-lookup"><span data-stu-id="c45f9-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="c45f9-108">Le proxy inscrit fait échouer l'appel à `QueryInterface`, car la tentative d'appel a été effectuée dans le contexte incorrect.</span><span class="sxs-lookup"><span data-stu-id="c45f9-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="c45f9-109">Un proxy détenu par OLE a retourné une erreur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c45f9-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c45f9-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="c45f9-110">Resolution</span></span>  
 <span data-ttu-id="c45f9-111">Consultez la documentation MSDN sur les règles COM.</span><span class="sxs-lookup"><span data-stu-id="c45f9-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c45f9-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="c45f9-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="c45f9-113">Si un appel à `QueryInterface` échoue, le contexte est changé et une nouvelle tentative d'appel à `QueryInterface` est effectuée pour déterminer si un contexte incorrect était en cause.</span><span class="sxs-lookup"><span data-stu-id="c45f9-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c45f9-114">Sortie</span><span class="sxs-lookup"><span data-stu-id="c45f9-114">Output</span></span>  
 <span data-ttu-id="c45f9-115">Nom managé de l'interface, GUID de l'interface et valeur HRESULT de l'échec.</span><span class="sxs-lookup"><span data-stu-id="c45f9-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c45f9-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="c45f9-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c45f9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c45f9-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c45f9-118">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="c45f9-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c45f9-119">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="c45f9-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
