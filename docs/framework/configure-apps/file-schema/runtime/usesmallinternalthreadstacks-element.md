---
title: "&lt;UseSmallInternalThreadStacks&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2558423b412333a4d6ac9f650ad8ff3dab449d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a>&lt;UseSmallInternalThreadStacks&gt; élément
Demandes de réduire la mémoire que le common language runtime (CLR) utilisent en spécifiant des tailles de pile explicites lorsqu’il crée certains threads qu’il utilise en interne, au lieu d’utiliser la taille de pile par défaut pour ces threads.  
  
 \<configuration > élément  
\<runtime > élément  
\<UseSmallInternalThreadStacks > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie s’il faut demander que le CLR utilisation explicite des tailles de pile au lieu de la taille de pile par défaut lorsqu’il crée certains threads qu’il utilise en interne. Les tailles de pile explicites sont inférieures à la taille de pile par défaut de 1 Mo.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|true|Demander des tailles de pile explicite.|  
|false|Utilisez la taille de pile par défaut. Ceci est la valeur par défaut pour le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément de configuration est utilisé pour demander l’utilisation réduite de la mémoire virtuelle dans un processus, car les tailles de threads explicites que le CLR utilise pour ses threads internes, si la demande est honorée, sont plus petites que la taille par défaut.  
  
> [!IMPORTANT]
>  Cet élément de configuration est une demande au CLR plutôt qu’une spécification absolue. Dans la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], la demande est honorée uniquement pour les x86 architecture. Cet élément peut complètement ignoré dans les futures versions du CLR ou remplacé par des tailles de pile explicites qui sont toujours utilisés pour les threads internes sélectionnés.  
  
 Spécification de que cet élément de configuration de transactions fiabilité pour une utilisation de mémoire virtuelle plus petite si le CLR répond à la demande, car la plus petite taille de pile peut augmenter dépasse plus probable.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment demander que la CLR utilisation explicite des tailles de pile pour certains threads qu’il utilise en interne.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
