---
title: "&lt;bypassTrustedAppStrongNames&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0343aef083076249325b9577f90964d066867f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a>&lt;bypassTrustedAppStrongNames&gt; élément
Spécifie s’il faut ignorer la validation des noms forts sur les assemblys de confiance totale sont chargés dans un niveau de confiance totale <xref:System.AppDomain>.  
  
 \<configuration>  
\<runtime >  
\<bypassTrustedAppStrongNames >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si la fonctionnalité de contournement qui évite la validation des noms forts pour les assemblys de confiance totale est activée. Lorsque cette fonctionnalité est activée, les noms forts ne sont pas validées sont correctes lorsque l’assembly est chargé. La valeur par défaut est `true`.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`true`|Les signatures avec nom fort sur les assemblys de confiance totale ne sont pas validées lorsque les assemblys sont chargés dans un niveau de confiance totale <xref:System.AppDomain>. Il s'agit de la valeur par défaut.|  
|`false`|Les signatures avec nom fort sur les assemblys de confiance totale sont validées lorsque les assemblys sont chargés dans un niveau de confiance totale <xref:System.AppDomain>. La signature de nom fort est vérifiée uniquement pour la vérification de signature ; Il n’est pas comparé à un autre nom fort pour une correspondance.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 La fonctionnalité de contournement de noms forts évite de vérification de signature de nom fort des assemblys de confiance totale.  
  
 Cette fonctionnalité s'applique à tout assembly signé avec un nom fort qui présente les caractéristiques suivantes :  
  
-   Confiance totale sans la <xref:System.Security.Policy.StrongName> preuve (par exemple, a `MyComputer` preuve de zone).  
  
-   Chargé dans un <xref:System.AppDomain> de confiance totale.  
  
-   Chargé à partir d'un emplacement sous la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> de cet <xref:System.AppDomain>.  
  
-   Sans signature différée.  
  
> [!NOTE]
>  Si cette fonctionnalité a été désactivée pour toutes les applications sur l’ordinateur à l’aide d’une clé de Registre, ce paramètre de fichier de configuration n’a aucun effet. Pour plus d’informations, consultez [Comment : désactiver la fonctionnalité de dérivation avec un nom fort](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier le comportement qui valide la signature de nom fort sur les assemblys de confiance totale.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Guide pratique pour désactiver la fonctionnalité consistant à ignorer les noms forts](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
