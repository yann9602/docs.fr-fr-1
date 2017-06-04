---
title: "invalidIUnknown MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid IUnknown pointer"
  - "InvalidIUnknown MDA"
  - "invalid IUnknown pointers"
  - "IUnknown pointers"
  - "managed debugging assistants (MDAs), invalid IUnknown pointer"
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# invalidIUnknown MDA
L'Assistant Débogage managé \(MDA\) `invalidIUnknown` est activé quand un pointeur `IUnknown` non valide est passé au code managé à partir du code natif.  Le pointeur `IUnknown` ne peut pas retourner un succès quand il est interrogé sur l'interface `IUnknown`.  
  
## Symptômes  
 Une erreur inattendue se produit quand un pointeur d'interface COM est marshalé pendant le marshaling d'argument.  
  
## Cause  
 Une implémentation incorrecte de `QueryInterface` sur l'interface COM a été passée au CLR.  
  
## Résolution  
 Corrigez l'implémentation de `QueryInterface`.  
  
## Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## Sortie  
 Description de l'erreur.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)