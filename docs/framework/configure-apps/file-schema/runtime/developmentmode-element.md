---
title: "&lt;developmentMode&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4573c3a5e0cf64996f2a4e109736d966b754494a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdevelopmentmodegt-element"></a>&lt;developmentMode&gt; élément
Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.  
  
 \<configuration>  
\<runtime >  
\<developmentMode >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**developerInstallation**|Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|  
  
## <a name="developerinstallation-attribute"></a>Attribut de developerInstallation  
  
|Valeur|Description|  
|-----------|-----------------|  
|**true**|Recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.|  
|**false**|Ne recherche pas les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH. Ceci est la valeur par défaut|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez ce paramètre uniquement au moment du développement. Le runtime ne vérifie pas les versions sur les assemblys avec nom fort trouvés dans DEVPATH. Elle utilise simplement le premier assembly qu’il trouve.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Comment : localiser des assemblys à l'aide de DEVPATH](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
