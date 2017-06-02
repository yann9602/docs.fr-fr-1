---
title: "invalidGCHandleCookie MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid cookies"
  - "cookies, invalid"
  - "managed debugging assistants (MDAs), invalid cookies"
  - "InvalidGCHandleCookie MDA"
  - "invalid cookies"
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# invalidGCHandleCookie MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `invalidGCHandleCookie` est activé lorsqu'une tentative de conversion d'un cookie <xref:System.IntPtr> non valide en un <xref:System.Runtime.InteropServices.GCHandle> est effectuée.  
  
## Symptômes  
 Comportement indéfini tel que les violations d'accès et l'altération de la mémoire lors des tentatives d'utilisation ou de récupération d'un <xref:System.Runtime.InteropServices.GCHandle> à partir d'un <xref:System.IntPtr>.  
  
## Cause  
 Le cookie est probablement non valide car il n'a pas été initialement créé à partir d'un <xref:System.Runtime.InteropServices.GCHandle>, il représente un <xref:System.Runtime.InteropServices.GCHandle> qui a déjà été libéré, il est un cookie pour un <xref:System.Runtime.InteropServices.GCHandle> dans un domaine d'application différent ou il a été marshalé en code natif en tant que <xref:System.Runtime.InteropServices.GCHandle> mais a été retourné au CLR en tant que <xref:System.IntPtr>, où une tentative de cast a été effectuée.  
  
## Résolution  
 Spécifiez un cookie <xref:System.IntPtr> valide pour le <xref:System.Runtime.InteropServices.GCHandle>.  
  
## Effet sur le runtime  
 Lorsque ce MDA est activé, le débogueur n'est plus en mesure de tracer les racines vers leurs objets car les valeurs du cookie retournées sont différentes de celles retournés lorsque le MDA n'est pas activé.  
  
## Sortie  
 La valeur du cookie <xref:System.IntPtr> non valide est signalée.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>   
 <xref:System.Runtime.InteropServices.GCHandle>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)