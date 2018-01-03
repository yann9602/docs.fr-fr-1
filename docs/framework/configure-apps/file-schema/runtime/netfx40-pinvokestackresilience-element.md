---
title: "&lt;NetFx40_PInvokeStackResilience&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17816ee6134dc6b3074256093c0cba07419baf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a>&lt;NetFx40_PInvokeStackResilience&gt; élément
Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.  
  
 \<configuration>  
\<runtime >  
< NetFx40_PInvokeStackResilience >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime détecte plateforme incorrect déclarations d’appel et résout automatiquement la pile au moment de l’exécution sur les plateformes 32 bits.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`0`|Le runtime utilise l’architecture introduite dans de marshaling d’interopérabilité plus rapide la [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], qui ne détecte pas et les déclarations d’appel de plateforme incorrect de correctif. Il s'agit de la valeur par défaut.|  
|`1`|Les runtime utilise les transitions lentes pour détecter et corriger la plateforme incorrecte les déclarations d’appel.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 Cet élément vous permet aux échanges plus rapidement le marshaling d’interopérabilité pour les déclarations d’appel de résilience d’exécution sur la plateforme incorrecte.  
  
 En commençant par le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], une architecture de marshaling d’interopérabilité simplifiée offre une amélioration significative des performances pour les transitions du code managé au code non managé. Dans les versions antérieures du .NET Framework, la plateforme incorrecte détectée de couche marshaling sur les plateformes 32 bits, les déclarations d’appel et corrigés automatiquement la pile. La nouvelle architecture de marshaling élimine cette étape. Par conséquent, les transitions sont très rapides, mais une déclaration non managé incorrectes peuvent provoquer un échec du programme.  
  
 Pour faciliter la détection des déclarations incorrectes pendant le développement, le débogage de Visual Studio a été amélioré. Le [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) assistant débogage managé (MDA) vous notifie de plateforme incorrect appel déclarations lorsque votre application s’exécute avec le débogueur attaché.  
  
 Pour les scénarios où votre application utilise des composants que vous ne pouvez pas recompiler et qu’avez incorrect non managé déclarations, vous pouvez utiliser la `NetFx40_PInvokeStackResilience` élément. Ajout de cet élément à votre fichier de configuration d’application avec `enabled="1"` opte pour un mode de compatibilité avec le comportement des versions antérieures du .NET Framework, au prix de transitions plus lentes. Les assemblys qui ont été compilés avec des versions antérieures du .NET Framework sont automatiquement choisis dans ce mode de compatibilité et n’avez pas besoin de cet élément.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment adopter une résistance accrue contre incorrect pour une application, au prix de transitions plus lentes entre les déclarations d’appel de plateforme de code managé et.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
