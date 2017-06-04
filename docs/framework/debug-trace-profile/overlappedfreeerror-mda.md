---
title: "overlappedFreeError MDA | Microsoft Docs"
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
  - "OverlappedFreeError MDA"
  - "overlapped free method call error"
  - "managed debugging assistants (MDAs), overlapped structures"
  - "overlapped structures"
  - "MDAs (managed debugging assistants), overlapped structures"
  - "freeing overlapped structures"
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# overlappedFreeError MDA
L'Assistant Débogage managé `overlappedFreeError` \(MDA\) est activé lorsque la méthode <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=fullName> est appelée avant la fin de l'opération avec chevauchement.  
  
## Symptômes  
 Accédez aux violations ou endommagement du tas récupéré par le garbage collector.  
  
## Cause  
 Une structure superposée a été libérée avant la fin de l'opération.  La fonction qui utilise le pointeur superposé peut écrire ultérieurement dans la structure, après qu'il a été libéré.  Cela peut provoquer l'endommagement de tas parce qu'un autre objet peut maintenant occuper cette région.  
  
 Ce MDA ne peut pas représenter d'erreur si l'opération superposée n'a pas démarré.  
  
## Résolution  
 Assurez\-vous que l'opération d'E\/S utilisant la structure superposée a terminé avant d'appeler la méthode <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29>.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  
  
## Sortie  
 L'exemple suivant illustre une sortie de cet Assistant Débogage managé.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'.  If the AppDomain is shut down, this can cause heap corruption when the async I/O completes.  The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack().  If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)