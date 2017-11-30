---
title: "Assistant Débogage managé invalidIUnknown"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 04fdc96168823397296449ebc25ccdded1ea55c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="invalidiunknown-mda"></a>Assistant Débogage managé invalidIUnknown
L'Assistant Débogage managé (MDA) `invalidIUnknown` est activé quand un pointeur `IUnknown` non valide est passé au code managé à partir du code natif. Le pointeur `IUnknown` ne peut pas retourner un succès quand il est interrogé sur l'interface `IUnknown`.  
  
## <a name="symptoms"></a>Symptômes  
 Une erreur inattendue se produit quand un pointeur d'interface COM est marshalé pendant le marshaling d'argument.  
  
## <a name="cause"></a>Cause  
 Une implémentation incorrecte de `QueryInterface` sur l'interface COM a été passée au CLR.  
  
## <a name="resolution"></a>Résolution  
 Corrigez l'implémentation de `QueryInterface`.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Sortie  
 Description de l'erreur.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling d'interopérabilité](../../../docs/framework/interop/interop-marshaling.md)
