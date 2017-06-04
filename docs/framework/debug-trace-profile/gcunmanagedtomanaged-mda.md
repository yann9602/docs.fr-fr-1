---
title: "gcUnmanagedToManaged MDA | Microsoft Docs"
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
  - "GC unmanaged to managed"
  - "transitioning threads unmanaged to managed code"
  - "GcUnmanagedToManaged MDA"
  - "threading [.NET Framework], garbage collection"
  - "managed debugging assistants (MDAs), garbage collection"
  - "threading [.NET Framework], managed debugging assistants"
  - "garbage collection, run-time errors"
  - "unmanaged to managed garbage collection"
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# gcUnmanagedToManaged MDA
L'Assistant Débogage managé \(MDA\) `gcUnmanagedToManaged` déclenche une opération garbage collection chaque fois qu'un thread effectue la transition du code non managé au code managé.  
  
## Symptômes  
 Une application exécutant des composants utilisateur non managés à l'aide de COM et d'appels de code non managé provoque une violation d'accès non déterministe dans le CLR.  
  
## Cause  
 Si une application exécute des composants utilisateur non managés, il se peut que ces composants aient endommagé le tas obtenu à l'issue d'une opération garbage collection.  Cela provoque une violation d'accès dans le CLR quand le garbage collector tente de parcourir le graphique d'objet.  
  
## Résolution  
 L'activation de cet assistant réduit la durée entre le moment où le composant non managé endommage le tas obtenu à l'issue d'une opération garbage collection et le moment de la violation d'accès en obligeant l'exécution d'une opération garbage collection avant chaque transition managée.  
  
## Effet sur le runtime  
 Provoque une opération garbage collection chaque fois qu'un thread effectue la transition du code non managé au code managé.  
  
## Sortie  
 Cet Assistant Débogage managé ne produit aucune sortie.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)