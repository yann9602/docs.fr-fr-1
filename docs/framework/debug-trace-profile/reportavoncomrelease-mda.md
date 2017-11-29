---
title: "Assistant Débogage managé reportAvOnComRelease"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de48fca818f8456627c9507756cc2d8a200c50e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="bdf39-102">Assistant Débogage managé reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="bdf39-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="bdf39-103">L'Assistant Débogage managé `reportAvOnComRelease` est activé quand des exceptions sont levées en raison d'erreurs de comptage de références utilisateur pendant une opération COM Interop et l'utilisation de la méthode <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinée avec des appels COM bruts.</span><span class="sxs-lookup"><span data-stu-id="bdf39-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bdf39-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="bdf39-104">Symptoms</span></span>  
 <span data-ttu-id="bdf39-105">Violations d'accès et endommagement de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="bdf39-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bdf39-106">Cause</span><span class="sxs-lookup"><span data-stu-id="bdf39-106">Cause</span></span>  
 <span data-ttu-id="bdf39-107">Parfois, une exception est levée en raison d'erreurs de comptage de références utilisateur pendant une opération COM Interop et l'utilisation de la méthode <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinée avec des appels COM bruts.</span><span class="sxs-lookup"><span data-stu-id="bdf39-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="bdf39-108">Normalement, cette exception est ignorée, car elle entraînerait une violation d'accès dans le CLR et l'arrêt de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="bdf39-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="bdf39-109">Quand cet Assistant est activé, les exceptions de ce type peuvent être détectées et signalées au lieu d'être simplement ignorées.</span><span class="sxs-lookup"><span data-stu-id="bdf39-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bdf39-110">Solution</span><span class="sxs-lookup"><span data-stu-id="bdf39-110">Resolution</span></span>  
 <span data-ttu-id="bdf39-111">Examinez votre code de comptage de références, ainsi que les clients natifs de votre objet pour déterminer s'ils contiennent des erreurs de comptage.</span><span class="sxs-lookup"><span data-stu-id="bdf39-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bdf39-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="bdf39-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="bdf39-113">Deux modes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="bdf39-113">Two modes are available.</span></span> <span data-ttu-id="bdf39-114">Si l'attribut `allowAv` a pour valeur `true`, l'Assistant empêche le runtime d'ignorer la violation d'accès.</span><span class="sxs-lookup"><span data-stu-id="bdf39-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="bdf39-115">Si l'attribut `allowAv` est défini sur `false` (valeur par défaut), le runtime ignore la violation d'accès, mais un message d'avertissement est présenté à l'utilisateur pour indiquer qu'une exception a été levée et ignorée.</span><span class="sxs-lookup"><span data-stu-id="bdf39-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bdf39-116">Sortie</span><span class="sxs-lookup"><span data-stu-id="bdf39-116">Output</span></span>  
 <span data-ttu-id="bdf39-117">Si possible, la sortie contient le vtable d'origine du pointeur d'interface COM.</span><span class="sxs-lookup"><span data-stu-id="bdf39-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="bdf39-118">Sinon, un message d'information apparaît.</span><span class="sxs-lookup"><span data-stu-id="bdf39-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bdf39-119">Configuration</span><span class="sxs-lookup"><span data-stu-id="bdf39-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bdf39-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdf39-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="bdf39-121">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="bdf39-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="bdf39-122">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="bdf39-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
