---
title: "invalidVariant MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid variant"
  - "VARIANT type errors"
  - "InvalidVariant MDA"
  - "invalid VARIANT types"
  - "managed debugging assistants (MDAs), invalid variant"
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# invalidVariant MDA
L'Assistant Débogage managé \(MDA\) `invalidVariant` est activé quand une structure `VARIANT` non valide est rencontrée lors d'un appel du code natif ou non managé au code managé.  
  
## Symptômes  
 Comportement inattendu pendant une transition entre du code natif et managé impliquant le marshaling d'une structure `VARIANT` en objet.  
  
## Cause  
 Le code natif passe une structure `VARIANT` incorrecte au code managé.  Le runtime tente de marshaler cette `VARIANT` en objet et active l'Assistant Débogage managé si la `VARIANT` n'est pas valide.  Exemples de structures `VARIANT` non valides : une structure `VARIANT` avec un `VARTYPE` VT\_EMPTY &#124; VT\_BYREF ou une structure `VARIANT` avec le `VARTYPE` VT\_VARIANT.  
  
## Résolution  
 Le code natif ou non managé qui passe la structure `VARIANT` doit s'assurer que la `VARIANT` est correcte et bien initialisée.  
  
## Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le comportement du runtime.  
  
## Sortie  
 Message de l'Assistant Débogage managé indiquant que le runtime a détecté qu'une structure `VARIANT` incorrecte a été passée au code managé par un module non managé.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)