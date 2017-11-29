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
ms.openlocfilehash: b33a3edc5780ecf07e7809ca327a304d748110f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokestackimbalance-mda"></a>Assistant Débogage managé pInvokeStackImbalance
L'Assistant Débogage managé (MDA) `pInvokeStackImbalance` est activé quand le CLR détecte que la profondeur de la pile après un appel de code non managé ne correspond pas à la profondeur de la pile attendue par rapport à la convention d'appel spécifiée dans l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute> et à la déclaration des paramètres dans la signature managée.  
  
> [!NOTE]
>  L'Assistant Débogage managé (MDA) `pInvokeStackImbalance` est implémenté uniquement pour les plateformes 32 bits x86.  
  
> [!NOTE]
>  Dans .NET Framework 3.5, l'Assistant Débogage managé (MDA) `pInvokeStackImbalance` est désactivé par défaut. Si vous utilisez le .NET Framework 3.5 avec Visual Studio 2005, l’Assistant Débogage managé (MDA) `pInvokeStackImbalance` figure dans la liste **Assistants Débogage managé** de la boîte de dialogue **Exceptions** (qui s’affiche quand vous cliquez sur **Exceptions** dans le menu **Déboguer**). Toutefois, le fait de cocher ou décocher la case **Levé** pour `pInvokeStackImbalance` ne permet pas d’activer ou de désactiver l’Assistant Débogage managé (MDA) ; cela détermine seulement si Visual Studio lève une exception quand cet Assistant est activé.  
  
## <a name="symptoms"></a>Symptômes  
 Une application rencontre une violation d'accès ou une altération de la mémoire pendant ou après un appel de code non managé.  
  
## <a name="cause"></a>Cause  
 Il se peut que la signature managée de l'appel de code non managé ne corresponde pas à la signature non managée de la méthode qui est appelée.  Cette incompatibilité peut être due au fait que la signature managée ne déclare pas le nombre correct de paramètres ou ne spécifie pas la taille appropriée pour les paramètres.  L'Assistant Débogage managé (MDA) peut également être activé parce que la convention d'appel, éventuellement spécifiée par l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute>, ne correspond pas à la convention d'appel non managée.  
  
## <a name="resolution"></a>Résolution  
 Vérifiez que la signature managée de l'appel de code non managé et la convention d'appel correspondent à la signature et à la convention d'appel de la cible native.  Essayez de spécifier explicitement la convention d'appel à la fois du côté managé et du côté non managé. Il est également possible, mais moins probable, que la fonction non managée ait déséquilibré la pile pour une raison quelconque, telle qu'un bogue dans le compilateur non managé.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Oblige tous les appels de code non managé à prendre le chemin d'accès non optimisé dans le CLR.  
  
## <a name="output"></a>Sortie  
 Le message de l'Assistant Débogage managé (MDA) donne le nom de l'appel de méthode d'appel de code non managé qui provoque le déséquilibre de la pile.  Voici un exemple de message d'un appel de code non managé sur la méthode `SampleMethod` :  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling d'interopérabilité](../../../docs/framework/interop/interop-marshaling.md)
