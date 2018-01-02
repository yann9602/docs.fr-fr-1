---
title: "&lt;gcAllowVeryLargeObjects&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5db777f147e2eca7644d5b5f1a4bc18c8401ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a>&lt;gcAllowVeryLargeObjects&gt; élément
Sur les plateformes 64 bits, autorise les tableaux dont la taille totale est supérieure à 2 gigaoctets (Go).  
  
 \<configuration > élément  
\<runtime > élément  
\<gcAllowVeryLargeObjects > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si les tableaux sont supérieures à 2 Go de taille totale sont activés sur des plateformes 64 bits.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Supérieure à 2 Go de taille totale des tableaux ne sont pas activés. Il s'agit de la valeur par défaut.|  
|`true`|Supérieure à 2 Go de taille totale des tableaux sont activés sur des plateformes 64 bits.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 Dans votre fichier de configuration d’application à l’aide de cet élément permet de tableaux supérieurs à 2 Go, mais ne modifie pas les autres limites sur la taille de l’objet ou de la taille du tableau :  
  
-   Le nombre maximal d’éléments dans un tableau est <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
-   L’index maximal dans n’importe quelle dimension unique est 2,147,483,591 (0x7FFFFFC7) pour les tableaux d’octets et les tableaux de structures d’un octet et 2,146,435,071 (0X7FEFFFFF) pour les autres types.  
  
-   La taille maximale pour les chaînes et autres objets non-tableau est inchangée.  
  
> [!CAUTION]
>  Avant d’activer cette fonctionnalité, vérifiez que votre application n’inclut pas de code unsafe qui suppose que tous les tableaux sont inférieures à 2 Go. Par exemple, du code qui utilise des tableaux en tant que les mémoires tampons unsafe peut-être susceptibles d’être dépassements de mémoire tampon si elle est écrite sur l’hypothèse que les tableaux ne dépassent pas 2 Go.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer cette fonctionnalité pour une application.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
