---
title: "&lt;applicationPool&gt; élément (paramètres Web)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 70119b3067342dc9bc93e0fb8a43a3242f2dacc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt; élément (paramètres Web)
Spécifie les paramètres de configuration qui sont utilisés par ASP.NET pour gérer le comportement au niveau du processus lorsqu’une application ASP.NET s’exécute en mode intégré sur [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou une version ultérieure.  
  
> [!IMPORTANT]
>  Cet élément et la fonctionnalité qu’il prend en charge uniquement si votre application ASP.NET est hébergée sur [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versions ultérieures.  
  
 \<configuration>  
\<System.Web >, élément (paramètres Web)  
\<applicationPool >, élément (paramètres Web)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|Spécifie le nombre de demandes simultanées ASP.NET autorise par UC.|  
|`maxConcurrentThreadsPerCPU`|Spécifie le nombre de threads simultané permettre être en cours d’exécution pour un pool d’applications pour chaque UC. Cela fournit une autre façon de contrôler l’accès concurrentiel ASP.NET, car vous pouvez limiter le nombre de threads managés qui peut être utilisé par l’UC pour traiter les demandes. Par défaut, ce paramètre est 0, ce qui signifie qu’ASP.NET ne limite pas le nombre de threads qui peuvent être créés par UC, bien que le pool de threads CLR limite également le nombre de threads qui peuvent être créés.|  
|`requestQueueLimit`|Spécifie le nombre maximal de demandes qui peuvent être en file d’attente pour ASP.NET dans un processus unique. Lorsque deux ou plusieurs applications de ASP.NET s’exécutent dans un pool d’applications unique, l’ensemble cumulatif des demandes effectuées sur n’importe quelle application dans le pool d’applications est soumis à ce paramètre.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Contient des informations sur la façon dont ASP.NET interagit avec une application hôte.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou une version ultérieure en mode intégré, cette combinaison d’éléments vous permet de configurer la manière dont ASP.NET gère les threads et les files d’attente des demandes lorsque l’application est hébergée dans un pool d’applications IIS. Si vous exécutez IIS 6 ou [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] en mode classique ou ISAPI, ces paramètres sont ignorés.  
  
 Le `applicationPool` paramètres s’appliquent à tous les pools d’applications qui s’exécutent sur une version particulière du .NET Framework. Les paramètres contenus dans un fichier aspnet.config. Il existe une version de ce fichier pour les versions 2.0 et 4.0 de .NET Framework. (Les versions 3.0 et 3.5 du .NET Framework partagent le fichier aspnet.config avec la version 2.0.)  
  
> [!IMPORTANT]
>  Si vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] sur [!INCLUDE[win7](../../../../../includes/win7-md.md)], vous pouvez configurer un fichier aspnet.config séparé pour chaque pool d’applications. Cela vous permet d’ajuster les performances des threads pour chaque pool d’applications.  
  
 Pour le `maxConcurrentRequestsPerCPU` , le paramètre par défaut de « 5000 » la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] désactive la limitation de requêtes contrôlée par ASP.NET, à moins que vous ayez réellement 5000 requêtes ou plus par UC. Le paramètre par défaut dépend à la place le pool de threads CLR pour gérer automatiquement l’accès concurrentiel par UC. Les applications qui utilisent beaucoup le traitement des demandes asynchrones ou qui possèdent de nombreuses requêtes longues bloquées sur le réseau d’e/s, bénéficieront de la limite par défaut accrue dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Paramètre `maxConcurrentRequestsPerCPU` à zéro désactive l’utilisation de threads managés pour le traitement des demandes ASP.NET. Lorsqu’une application s’exécute dans un pool d’applications IIS, les demandes restent sur le thread d’e/s IIS et par conséquent la concurrence est limitée par les paramètres de thread IIS.  
  
 Le `requestQueueLimit` paramètre fonctionne de la même façon que les `requestQueueLimit` attribut de la [processModel](http://msdn.microsoft.com/en-us/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) élément, qui est définie dans les fichiers Web.config pour les applications ASP.NET. Toutefois, le `requestQueueLimit` paramètre dans un fichier aspnet.config substitue le `requestQueueLimit` définition dans un fichier Web.config. En d’autres termes, si les deux attributs sont définis (par défaut, la valeur est true), la `requestQueueLimit` paramètre dans le fichier aspnet.config est prioritaire.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer le comportement au niveau du processus ASP.NET dans le fichier aspnet.config dans les circonstances suivantes :  
  
-   L’application est hébergée dans un [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] pool d’applications.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)]s’exécute en mode intégré.  
  
-   À l’aide de l’application est la [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou une version ultérieure.  
  
 Les valeurs dans l’exemple sont les valeurs par défaut.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms||  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## <a name="see-also"></a>Voir aussi  
 [\<system.web>, élément (paramètres web)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
