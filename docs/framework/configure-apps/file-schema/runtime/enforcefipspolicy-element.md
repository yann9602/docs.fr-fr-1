---
title: "&lt;enforceFIPSPolicy&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd593c17d752b35919985aad37f675c62e6ce34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;enforceFIPSPolicy&gt; élément
Indique s’il faut appliquer la condition de configuration d’ordinateur selon laquelle les algorithmes de chiffrement doivent être conformes aux normes FIPS (Federal Information Processing Standard).  
  
 \<configuration > élément  
\<runtime > élément  
\<enforceFIPSPolicy > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie s’il faut activer la mise en œuvre d’une spécification de configuration d’ordinateur que les algorithmes de chiffrement doivent être conformes à la norme FIPS.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`true`|Si votre ordinateur est configuré pour exiger des algorithmes de chiffrement conformes à FIPS, cette spécification est appliquée. Si une classe implémente un algorithme qui n’est pas conforme à la norme FIPS, les constructeurs ou `Create` méthodes pour cette classe lever des exceptions lorsqu’elles sont exécutées sur cet ordinateur. Il s'agit de la valeur par défaut.|  
|`false`|Les algorithmes de chiffrement qui sont utilisés par l’application ne sont pas requis pour être conforme à la norme FIPS, quelle que soit la configuration de l’ordinateur.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 À compter de .NET Framework 2.0, la création de classes qui implémentent des algorithmes de chiffrement est contrôlée par la configuration de l’ordinateur. Si l’ordinateur est configuré pour exiger des algorithmes pour être conforme à la norme FIPS, et une classe qui implémente un algorithme qui n’est pas conforme à la norme FIPS, toute tentative pour créer une instance de cette classe lève une exception. Constructeurs lèvent une <xref:System.InvalidOperationException> exception, et `Create` méthodes lèvent une <xref:System.Reflection.TargetInvocationException> exception avec une exception interne <xref:System.InvalidOperationException> exception.  
  
 Si votre application s’exécute sur les ordinateurs dont les configurations requièrent une conformité à la norme FIPS et que votre application utilise un algorithme qui n’est pas conforme à la norme FIPS, vous pouvez utiliser cet élément dans votre fichier de configuration pour empêcher le common language runtime (CLR) à partir de appliquer la conformité FIPS. Cet élément a été introduit dans le [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment empêcher le CLR d’appliquer la conformité FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Modèle de chiffrement](../../../../../docs/standard/security/cryptography-model.md)
