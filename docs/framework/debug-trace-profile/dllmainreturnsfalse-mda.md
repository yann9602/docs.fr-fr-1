---
title: "Assistant Débogage managé dllMainReturnsFalse"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb5de2b1c41d102fbf9fc47db0ff3d8bd72a3bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dllmainreturnsfalse-mda"></a>Assistant Débogage managé dllMainReturnsFalse
L’Assistant Débogage managé `dllMainReturnsFalse` est activé si la fonction `DllMain` managée d’un assembly utilisateur, appelée avec la raison DLL_PROCESS_ATTACH, retourne FALSE.  
  
## <a name="symptoms"></a>Symptômes  
 La fonction `DllMain` a retourné FALSE, indiquant qu’elle ne s’est pas exécuté correctement. Cela peut entraîner des problèmes indéterminés, car les fonctions `DllMain` contiennent généralement du code d’initialisation important.  
  
## <a name="cause"></a>Cause  
 La fonction `DllMain` est appelée avec la raison DLL_PROCESS_ATTACH pour l’initialisation de DLL lors du chargement. Si elle retourne FALSE, cela signifie que l’initialisation de la DLL a échoué.  
  
## <a name="resolution"></a>Résolution  
 Analysez le code de la fonction `DllMain` de la DLL ayant échoué, et identifiez la cause de l’échec d’initialisation.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le CLR. Il fournit uniquement des données sur la valeur de retour pour `DllMain`.  
  
## <a name="output"></a>Sortie  
 Un message indiquant qu’une fonction `DllMain`, appelée pour la raison DLL_PROCESS_ATTACH, a retourné FALSE. Notez que cet Assistant Débogage managé est activé uniquement si `DllMain` est implémenté dans le code managé.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
