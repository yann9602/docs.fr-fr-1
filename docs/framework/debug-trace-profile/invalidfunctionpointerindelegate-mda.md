---
title: invalidFunctionPointerInDelegate (MDA)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c448f1e60570ae8eff9c0af0dfc942c1ed5d7599
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate (MDA)
L'Assistant Débogage managé `invalidFunctionPointerInDelegate` est activé quand un pointeur de fonction non valide est transmis pour créer un délégué sur un pointeur de fonction natif.  
  
## <a name="symptoms"></a>Symptômes  
 Violations d'accès ou endommagement de mémoire inattendu pendant l'utilisation d'un délégué sur un pointeur de fonction.  
  
## <a name="cause"></a>Cause  
 Un pointeur de fonction non valide a été spécifié.  
  
## <a name="resolution"></a>Solution  
 Spécifiez un pointeur de fonction valide.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Sortie  
 Pointeur de fonction non valide.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Marshaling d’interopérabilité](../../../docs/framework/interop/interop-marshaling.md)

