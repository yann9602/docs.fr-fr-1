---
title: "gcManagedToUnmanaged MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MDAs (managed debugging assistants), garbage collection"
  - "GcManagedToUnmanaged MDA"
  - "GC managed to unmanaged"
  - "transitioning threads managed to unmanaged code"
  - "threading [.NET Framework], garbage collection"
  - "managed to unmanaged garbage collection"
  - "managed debugging assistants (MDAs), garbage collection"
  - "threading [.NET Framework], managed debugging assistants"
  - "garbage collection, run-time errors"
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# gcManagedToUnmanaged MDA
L'Assistant Débogage managé \(MDA\) `gcManagedToUnmanaged` déclenche une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.  
  
## Symptômes  
 Un composant utilisateur non managé lève une violation d'accès lors de la tentative d'utilisation d'un objet managé qui avait été exposé à COM.  L'objet COM semble avoir été libéré.  La violation d'accès est non déterministe.  
  
## Cause  
 Si un composant non managé n'effectue pas correctement le décompte de références d'un objet COM managé, le runtime peut collecter un objet managé exposé à COM lorsque le composant non managé détient encore une référence à l'objet.  Le runtime appelle <xref:System.Runtime.InteropServices.Marshal.Release%2A> pendant les opérations garbage collection. Par conséquent, si le composant utilisateur a recours à l'objet avant l'opération garbage collection, il n'aura pas encore été collecté.  Cela explique le non\-déterminisme.  
  
## Résolution  
 L'activation de cet assistant réduit le laps de temps entre le moment où l'objet peut participer à une collection et le moment où <xref:System.Runtime.InteropServices.Marshal.Release%2A> est appelé, ce qui facilite la localisation du composant non managé qui tente en premier d'accéder à l'objet récupéré par le garbage collector.  
  
## Effet sur le runtime  
 Provoque une opération garbage collection chaque fois qu'un thread effectue la transition du code managé au code non managé.  
  
## Sortie  
 Cet Assistant Débogage managé ne produit aucune sortie.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)   
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)