---
title: "Assistant Débogage managé marshalCleanupError"
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
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ad81faae235513b5d7c6665c3598a443711a0d6d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="marshalcleanuperror-mda"></a>Assistant Débogage managé marshalCleanupError
L'Assistant Débogage managé `marshalCleanupError` est activé quand le Common Language Runtime (CLR) rencontre une erreur pendant une tentative de nettoyage de la mémoire et des structures temporaires utilisées pour le marshaling de types de données entre des limites de code native et managé.  
  
## <a name="symptoms"></a>Symptômes  
 Une fuite de mémoire se produit en cas de transitions de code natif et managé, de non-restauration d'état d'exécution tel que la culture de thread ou d'erreurs de nettoyage <xref:System.Runtime.InteropServices.SafeHandle>.  
  
## <a name="cause"></a>Cause  
 Une erreur inattendue s'est produite pendant le nettoyage des structures temporaires.  
  
## <a name="resolution"></a>Solution  
 Examinez toutes les implémentations de marshaleur personnalisé, de finaliseur et de destructeur <xref:System.Runtime.InteropServices.SafeHandle> pour déterminer si elles contiennent des erreurs.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR.  
  
## <a name="output"></a>Sortie  
 Message indiquant l'opération ayant échoué pendant le nettoyage.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Marshaling d’interopérabilité](../../../docs/framework/interop/interop-marshaling.md)

