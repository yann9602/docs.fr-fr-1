---
title: "&lt;relativeBindForResources&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8409b1fe86776397ceb3db5b338fb8aaadef9cbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativeBindForResources&gt; élément
Optimise la sonde pour les assemblys satellites.  
  
 \<configuration > élément  
\<runtime > élément  
\<relativeBindForResources > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le common language runtime optimise la sonde pour les assemblys satellites.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Le runtime n’optimise pas la sonde pour les assemblys satellites. Valeur par défaut.|  
|`true`|Le runtime optimise la sonde pour les assemblys satellites.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 En règle générale, le Gestionnaire de ressources tente de détecter des ressources, comme indiqué dans le [empaquetage et déploiement de ressources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) rubrique. Cela signifie que lorsque le Gestionnaire de ressources détecte une version localisée particulière d’une ressource, il peut rechercher dans le global assembly cache, de rechercher dans un dossier spécifique à la culture dans la requête de base, de code de l’application Windows Installer pour les assemblys satellites et déclencher le <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement. Le `<relativeBindForResources>` élément optimise la méthode dans laquelle le Gestionnaire de ressources tente de détecter les assemblys satellites. Elle peut améliorer les performances lors de la détection pour les ressources dans les conditions suivantes :  
  
-   Lorsque l’assembly satellite est déployé dans le même emplacement que l’assembly de code. En d’autres termes, si l’assembly de code est installé dans le global assembly cache, les assemblys satellites doivent également être installés. Si l’assembly de code est installé dans la base de code de l’application, les assemblys satellites doivent également être installés dans un dossier spécifique à la culture dans la base de code.  
  
-   Lorsque le programme d’installation de Windows n’est pas utilisé ou rarement utilisé pour l’installation à la demande des assemblys satellites.  
  
-   Lorsque le code d’application ne gère pas la <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.  
  
 Définition de la `enabled` attribut de la `<relativeBindForResources>` élément à `true` optimise les sondage du Gestionnaire de ressources pour les assemblys satellites comme suit :  
  
-   Elle utilise l’emplacement de l’assembly de code parent sondage de l’assembly satellite.  
  
-   Il n’interroge pas le programme d’installation de Windows pour les assemblys satellites.  
  
-   Elle ne déclenche pas le <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de ressources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
