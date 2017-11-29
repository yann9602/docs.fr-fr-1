---
title: "&lt;legacyCorruptedStateExceptionsPolicy&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4379f6f38c886504905483cefd7c7a6bbd519ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a>&lt;legacyCorruptedStateExceptionsPolicy&gt; élément
Spécifie si le common language runtime permet au code managé d’intercepter les violations d’accès et d’autres exceptions d’état endommagé.  
  
 \<configuration>  
\<runtime >  
\<legacyCorruptedStateExceptionsPolicy >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie que l’application interceptera endommager les échecs d’état d’exception telles que des violations d’accès.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|L’application n’intercepte pas endommager les échecs d’état d’exception telles que des violations d’accès. Il s'agit de la valeur par défaut.|  
|`true`|L’application interceptera endommager les échecs d’état d’exception telles que des violations d’accès.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 Dans le .NET Framework version 3.5 et versions antérieure, le common language runtime autorise le code managé intercepter les exceptions levées par les États de processus endommagés. Une violation d’accès est un exemple de ce type d’exception.  
  
 En commençant par le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]managé code n’intercepte plus ces types d’exceptions dans `catch` blocs. Toutefois, vous pouvez remplacer cette modification et mettre à jour de la gestion des exceptions d’état endommagé de deux manières :  
  
-   Définir le `<legacyCorruptedStateExceptionsPolicy>` l’élément `enabled` attribut `true`. Ce paramètre de configuration est appliquée au niveau du processus et affecte toutes les méthodes.  
  
 ou  
  
-   Appliquer le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> d’attribut à la méthode qui contient les exceptions `catch` bloc.  
  
 Cet élément de configuration est uniquement disponible dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier que l’application doit rétablir le comportement avant le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]et d’intercepter l’altération de tous les échecs d’exception état.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
