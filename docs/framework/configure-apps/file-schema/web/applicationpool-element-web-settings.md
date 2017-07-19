---
title: "&lt;applicationPool&gt;, &#233;l&#233;ment (Param&#232;tres Web) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<applicationPool> (élément)"
  - "applicationPool (élément)"
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;applicationPool&gt;, &#233;l&#233;ment (Param&#232;tres Web)
Spécifie les paramètres de configuration utilisés par ASP.NET pour gérer le comportement au niveau du processus lorsqu'une application ASP.NET s'exécute en mode intégré sur [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou une version ultérieure.  
  
> [!IMPORTANT]
>  Cet élément et la fonctionnalité qu'il prend en charge fonctionnent uniquement si votre application ASP.NET est hébergée sur [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versions ultérieures.  
  
## Syntaxe  
  
```  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|Spécifie combien de demandes simultanées ASP.NET autorise par UC.|  
|`maxConcurrentThreadsPerCPU`|Spécifie combien de threads simultanés peuvent s'exécuter pour un pool d'applications pour chaque UC.  Cela fournit une autre manière de contrôler l'accès concurrentiel ASP.NET, car vous pouvez limiter le nombre de threads managés par UC pouvant être utilisés pour servir les demandes.  Par défaut, ce paramètre a la valeur 0, ce qui signifie qu'ASP.NET ne limite pas le nombre de threads par UC pouvant être créés, bien que le pool de threads CLR limite également le nombre de threads qui peuvent être créés.|  
|`requestQueueLimit`|Spécifie le nombre maximal de demandes qui peuvent être mises en file d'attente pour ASP.NET dans un processus unique.  Lorsque deux applications ASP.NET ou plus s'exécutent dans un pool d'applications unique, l'ensemble cumulatif des demandes qui sont faites à une application dans le pool d'applications est soumis à ce paramètre.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.web\>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Contient des informations sur la manière dont ASP.NET interagit avec une application hôte.|  
  
## Notes  
 Lorsque vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou une version ultérieure en mode intégré, cette combinaison d'éléments vous permet de configurer la manière dont ASP.NET gère les threads et met en file d'attente des demandes lorsque l'application est hébergée dans un pool d'applications IIS.  Si vous exécutez IIS 6 ou [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] en mode classique ou ISAPI, ces paramètres sont ignorés.  
  
 Les paramètres `applicationPool` s'appliquent à tous les pools d'applications qui s'exécutent sur une version particulière du .NET Framework.  Ces paramètres sont contenus dans un fichier aspnet.config.  Il existe une version de ce fichier pour les versions 2.0 et 4 du .NET Framework. \(Les versions 3.0 et 3.5 du .NET Framework partagent le fichier aspnet.config avec la version 2.0.\)  
  
> [!IMPORTANT]
>  Si vous exécutez [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] sur [!INCLUDE[win7](../../../../../includes/win7-md.md)], vous pouvez configurer un fichier aspnet.config séparé pour chaque pool d'applications.  Cela vous permet d'ajuster les performances des threads pour chaque pool d'applications.  
  
 Pour le paramètre `maxConcurrentRequestsPerCPU`, le paramètre par défaut "5000" dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] désactive la limitation de requêtes contrôlée par ASP.NET, à moins que vous ayez réellement 5000 requêtes ou plus par UC.  Le paramètre par défaut dépend en fait du pool de threads CLR pour gérer automatiquement l'accès concurrentiel par UC.  Les applications qui utilisent beaucoup le traitement des demandes asynchrones ou qui possèdent de nombreuses requêtes longues bloquées sur les E\/S réseau profiteront de l'augmentation de la limite par défaut dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  L'affectation de la valeur zéro à `maxConcurrentRequestsPerCPU` désactive l'utilisation des threads managés pour le traitement des demandes ASP.NET.  Lorsqu'une application s'exécute dans un pool d'applications IIS, les demandes restent sur le thread d'E\/S IIS ; l'accès concurrentiel est donc limité par les paramètres de thread IIS.  
  
 Le paramètre `requestQueueLimit` fonctionne de la même manière que l'attribut `requestQueueLimit` de l'élément [processModel](http://msdn.microsoft.com/fr-fr/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d), défini dans les fichiers Web.config pour les applications ASP.NET.  Toutefois, le paramètre `requestQueueLimit` dans un fichier aspnet.config substitue le paramètre `requestQueueLimit` dans un fichier Web.config.  En d'autres termes, si les deux attributs sont définis \(par défaut, la valeur est true\), le paramètre `requestQueueLimit` dans le fichier aspnet.config est prioritaire.  
  
## Exemple  
 L'exemple suivant indique comment configurer le comportement au niveau du processus d'ASP.NET dans le fichier aspnet.config dans les circonstances suivantes :  
  
-   L'application est hébergée dans un pool d'applications [!INCLUDE[iisver](../../../../../includes/iisver-md.md)].  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] s'exécute en mode intégré.  
  
-   L'application utilise [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]ou une version ultérieure.  
  
 Les valeurs dans l'exemple sont les valeurs par défaut.  
  
```  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## Informations sur les éléments  
  
|||  
|-|-|  
|Espace de noms||  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## Voir aussi  
 [\<system.web\>, élément \(Paramètres Web\)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)