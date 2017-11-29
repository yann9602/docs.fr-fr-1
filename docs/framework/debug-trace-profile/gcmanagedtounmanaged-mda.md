---
title: "Assistant Débogage managé gcManagedToUnmanaged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1aa528eb2acc872b1956edef3af3724bb3b54d67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gcmanagedtounmanaged-mda"></a>Assistant Débogage managé gcManagedToUnmanaged
L'Assistant Débogage managé (MDA) `gcManagedToUnmanaged` déclenche une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.  
  
## <a name="symptoms"></a>Symptômes  
 Un composant utilisateur non managé lève une violation d'accès lors de la tentative d'utilisation d'un objet managé qui avait été exposé à COM. L'objet COM semble avoir été libéré. La violation d'accès est non déterministe.  
  
## <a name="cause"></a>Cause  
 Si un composant non managé n'effectue pas correctement le décompte de références d'un objet COM managé, le runtime peut collecter un objet managé exposé à COM lorsque le composant non managé détient encore une référence à l'objet. Le runtime appelle <xref:System.Runtime.InteropServices.Marshal.Release%2A> pendant les opérations garbage collection. Par conséquent, si le composant utilisateur a recours à l'objet avant l'opération garbage collection, il n'aura pas encore été collecté. Cela explique le non-déterminisme.  
  
## <a name="resolution"></a>Résolution  
 L'activation de cet assistant réduit le laps de temps entre le moment où l'objet peut participer à une collection et le moment où <xref:System.Runtime.InteropServices.Marshal.Release%2A> est appelé, ce qui facilite la localisation du composant non managé qui tente en premier d'accéder à l'objet récupéré par le garbage collector.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Provoque une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.  
  
## <a name="output"></a>Sortie  
 Cet Assistant Débogage managé ne produit aucune sortie.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling d'interopérabilité](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
