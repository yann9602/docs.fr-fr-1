---
title: "&lt;gcConcurrent&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 254b3be8f270a9186377b264094c919314efb27f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltgcconcurrentgt-element"></a>&lt;gcConcurrent&gt; élément
Spécifie si le common language runtime exécute l’opération garbage collection sur un thread distinct.  
  
 \<configuration>  
\<runtime >  
\<gcConcurrent >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime exécute l'opération garbage collection simultanément.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’exécute pas l’opération garbage collection simultanément.|  
|`true`|Exécute l’opération garbage collection simultanément. Il s'agit de la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Dans les versions antérieures à .NET Framework 4, le garbage collection de station de travail prenait en charge le garbage collection simultané, qui exécutait l’opération garbage collection en arrière-plan sur un thread distinct. Dans .NET Framework 4, le garbage collection simultané a été remplacé par le garbage collection d'arrière-plan pour effectuer l'opération de la même manière. Depuis .NET Framework 4.5, le garbage collection d'arrière-plan est disponible dans le garbage collection de serveur. L'élément `<gcConcurrent>` contrôle si le runtime exécute le garbage collection simultané ou d'arrière-plan, s'il est disponible, ou s'il exécute le garbage collection de premier plan.  
  
> [!WARNING]
>  Depuis .NET Framework 4, le garbage collection simultané est remplacé par le garbage collection d’arrière-plan. Les termes du contrat *simultanées* et *arrière-plan* sont utilisés indifféremment dans la documentation .NET Framework. Pour désactiver le garbage collection d'arrière-plan, utilisez l'élément `<gcConcurrent>` comme indiqué dans cet article.  
  
 Par défaut, le runtime utilise le garbage collection simultané ou d'arrière-plan, dont la latence est optimisée. Si votre application implique une grande interaction avec l'utilisateur, laissez le garbage collection simultané activé pour minimiser le temps d'interruption de l'application pendant l'exécution de l'opération garbage collection. Si vous définissez l'attribut `enabled` de l'élément `<gcConcurrent>` avec la valeur `false`, le runtime utilise le garbage collection non simultané, dont le débit est optimisé. Le fichier de configuration suivant désactive le garbage collection d'arrière-plan.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Le paramètre `<gcConcurrentSetting>` qui figure dans le fichier de configuration de l'ordinateur définit la valeur par défaut de toutes les applications .NET Framework. Ce paramètre se substitue au paramètre du fichier de configuration de l'application.  
  
 Pour plus d’informations sur simultané et garbage collection d’arrière-plan, consultez la section « le garbage collection simultané » dans le [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md) rubrique.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant active le garbage collection simultané.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Principes de base du Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md)
