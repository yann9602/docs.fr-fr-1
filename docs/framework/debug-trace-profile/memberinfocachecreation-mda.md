---
title: "Assistant Débogage managé memberInfoCacheCreation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1aeda59172e52c9880b39d6bf94ea9685a0203c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="memberinfocachecreation-mda"></a>Assistant Débogage managé memberInfoCacheCreation
L’Assistant Débogage managé `memberInfoCacheCreation` est activé quand le cache <xref:System.Reflection.MemberInfo> est créé. Il s’agit d’une indication forte d’un programme qui utilise des fonctionnalités de réflexion coûteuses en ressources.  
  
## <a name="symptoms"></a>Symptômes  
 La plage de travail d’un programme augmente, car il utilise une réflexion coûteuse en ressources.  
  
## <a name="cause"></a>Cause  
 Les opérations de réflexion qui impliquent des objets <xref:System.Reflection.MemberInfo> sont considérées comme coûteuses en ressources, car elles doivent lire les métadonnées stockées dans des pages peu consultées et elles indiquent généralement que le programme utilise un type de scénario à liaison tardive.  
  
## <a name="resolution"></a>Résolution  
 Vous pouvez déterminer où la réflexion est utilisée dans votre programme en activant cet Assistant Débogage managé puis en exécutant votre code dans un débogueur, ou en effectuant un attachement avec un débogueur quand l’Assistant Débogage managé est activé. Avec un débogueur, vous obtenez une arborescence des appels de procédure indiquant où le cache <xref:System.Reflection.MemberInfo> a été créé et, à partir de là, vous pouvez déterminer où votre programme utilise la réflexion.  
  
 La résolution dépend des objectifs du code. Cet Assistant Débogage managé vous avertit que votre programme a un scénario à liaison tardive. Vous pouvez alors déterminer si vous pouvez substituer un scénario à liaison anticipée ou considérer les performances du scénario à liaison tardive.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé est activé pour chaque cache <xref:System.Reflection.MemberInfo> créé. L’impact sur les performances est négligeable.  
  
## <a name="output"></a>Sortie  
 L’Assistant Débogage managé génère un message indiquant que le cache <xref:System.Reflection.MemberInfo> a été créé. Pour obtenir une arborescence des appels de procédure montrant l’endroit où votre programme utilise la réflexion, utilisez un débogueur.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple de code active l’Assistant Débogage managé `memberInfoCacheCreation`.  
  
```  
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection.MemberInfo>  
 [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
