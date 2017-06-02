---
title: "invalidFunctionPointerInDelegate MDA | Microsoft Docs"
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
  - "invalidFunctionPointerInDelegate MDA"
  - "managed debugging assistants (MDAs), invalid function pointer to delegates"
  - "MDAs (managed debugging assistants), invalid function pointer to delegates"
  - "function pointers, invalid"
  - "marshaling, run-time errors"
  - "managed debugging assistants (MDAs), marshaling"
  - "MDAs (managed debugging assistants), marshaling"
  - "invalid function pointers"
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# invalidFunctionPointerInDelegate MDA
L'Assistant Débogage managé `invalidFunctionPointerInDelegate` est activé quand un pointeur de fonction non valide est transmis pour créer un délégué sur un pointeur de fonction natif.  
  
## Symptômes  
 Violations d'accès ou endommagement de mémoire inattendu pendant l'utilisation d'un délégué sur un pointeur de fonction.  
  
## Cause  
 Un pointeur de fonction non valide a été spécifié.  
  
## Solution  
 Spécifiez un pointeur de fonction valide.  
  
## Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## Sortie  
 Pointeur de fonction non valide.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)