---
title: "Assistant Débogage managé pInvokeStackImbalance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9da05a84568a6168ed9f450afa48aa6864ed575
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="0622f-102">Assistant Débogage managé pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="0622f-102">pInvokeStackImbalance MDA</span></span>
<span data-ttu-id="0622f-103">L'Assistant Débogage managé (MDA) `pInvokeStackImbalance` est activé quand le CLR détecte que la profondeur de la pile après un appel de code non managé ne correspond pas à la profondeur de la pile attendue par rapport à la convention d'appel spécifiée dans l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute> et à la déclaration des paramètres dans la signature managée.</span><span class="sxs-lookup"><span data-stu-id="0622f-103">The `pInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute as well as the declaration of the parameters in the managed signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0622f-104">L'Assistant Débogage managé (MDA) `pInvokeStackImbalance` est implémenté uniquement pour les plateformes 32 bits x86.</span><span class="sxs-lookup"><span data-stu-id="0622f-104">The `pInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0622f-105">Dans .NET Framework 3.5, l'Assistant Débogage managé (MDA) `pInvokeStackImbalance` est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="0622f-105">In the .NET Framework version 3.5, the `pInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="0622f-106">Si vous utilisez le .NET Framework 3.5 avec Visual Studio 2005, l’Assistant Débogage managé (MDA) `pInvokeStackImbalance` figure dans la liste **Assistants Débogage managé** de la boîte de dialogue **Exceptions** (qui s’affiche quand vous cliquez sur **Exceptions** dans le menu **Déboguer**).</span><span class="sxs-lookup"><span data-stu-id="0622f-106">When you use the .NET Framework version 3.5 with Visual Studio 2005, the `pInvokeStackImbalance` MDA will appear in the **Managed Debugging Assistants** list in the **Exceptions** dialog box (which is displayed when you click **Exceptions** on the **Debug** menu).</span></span> <span data-ttu-id="0622f-107">Toutefois, le fait de cocher ou décocher la case **Levé** pour `pInvokeStackImbalance` ne permet pas d’activer ou de désactiver l’Assistant Débogage managé (MDA) ; cela détermine seulement si Visual Studio lève une exception quand cet Assistant est activé.</span><span class="sxs-lookup"><span data-stu-id="0622f-107">However, selecting or clearing the **Thrown** check box for `pInvokeStackImbalance` does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0622f-108">Symptômes</span><span class="sxs-lookup"><span data-stu-id="0622f-108">Symptoms</span></span>  
 <span data-ttu-id="0622f-109">Une application rencontre une violation d'accès ou une altération de la mémoire pendant ou après un appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="0622f-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0622f-110">Cause</span><span class="sxs-lookup"><span data-stu-id="0622f-110">Cause</span></span>  
 <span data-ttu-id="0622f-111">Il se peut que la signature managée de l'appel de code non managé ne corresponde pas à la signature non managée de la méthode qui est appelée.</span><span class="sxs-lookup"><span data-stu-id="0622f-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="0622f-112">Cette incompatibilité peut être due au fait que la signature managée ne déclare pas le nombre correct de paramètres ou ne spécifie pas la taille appropriée pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="0622f-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="0622f-113">L'Assistant Débogage managé (MDA) peut également être activé parce que la convention d'appel, éventuellement spécifiée par l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute>, ne correspond pas à la convention d'appel non managée.</span><span class="sxs-lookup"><span data-stu-id="0622f-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0622f-114">Résolution</span><span class="sxs-lookup"><span data-stu-id="0622f-114">Resolution</span></span>  
 <span data-ttu-id="0622f-115">Vérifiez que la signature managée de l'appel de code non managé et la convention d'appel correspondent à la signature et à la convention d'appel de la cible native.</span><span class="sxs-lookup"><span data-stu-id="0622f-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="0622f-116">Essayez de spécifier explicitement la convention d'appel à la fois du côté managé et du côté non managé.</span><span class="sxs-lookup"><span data-stu-id="0622f-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="0622f-117">Il est également possible, mais moins probable, que la fonction non managée ait déséquilibré la pile pour une raison quelconque, telle qu'un bogue dans le compilateur non managé.</span><span class="sxs-lookup"><span data-stu-id="0622f-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0622f-118">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="0622f-118">Effect on the Runtime</span></span>  
 <span data-ttu-id="0622f-119">Oblige tous les appels de code non managé à prendre le chemin d'accès non optimisé dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="0622f-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0622f-120">Sortie</span><span class="sxs-lookup"><span data-stu-id="0622f-120">Output</span></span>  
 <span data-ttu-id="0622f-121">Le message de l'Assistant Débogage managé (MDA) donne le nom de l'appel de méthode d'appel de code non managé qui provoque le déséquilibre de la pile.</span><span class="sxs-lookup"><span data-stu-id="0622f-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span>  <span data-ttu-id="0622f-122">Voici un exemple de message d'un appel de code non managé sur la méthode `SampleMethod` :</span><span class="sxs-lookup"><span data-stu-id="0622f-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a><span data-ttu-id="0622f-123">Configuration</span><span class="sxs-lookup"><span data-stu-id="0622f-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0622f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0622f-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="0622f-125">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="0622f-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="0622f-126">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="0622f-126">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
