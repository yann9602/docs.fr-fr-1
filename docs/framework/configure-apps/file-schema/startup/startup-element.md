---
title: "&lt;startup&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#startup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<startup> (élément)"
  - "balises conteneurs, <startup> (élément)"
  - "startup (élément)"
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: 19
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 19
---
# &lt;startup&gt;, &#233;l&#233;ment
Spécifie les informations de démarrage du common language runtime.  
  
## Syntaxe  
  
```  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|Attribut facultatif.<br /><br /> Spécifie s'il faut activer la stratégie d'activation de l'exécution [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] ou utiliser la stratégie d'activation [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
## Attribut useLegacyV2RuntimeActivationPolicy  
  
|Valeur|Description|  
|------------|-----------------|  
|`true`|Activer la stratégie d'activation de l'exécution [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] pour le runtime choisi, ce qui revient à lier les techniques d'activation du runtime héritées \(comme la [fonction CorBindToRuntimeEx](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)\) au runtime choisi dans le fichier de configuration, au lieu d'avoir recours aux limites maximales d'utilisation du CLR version 2.0.  Ainsi, si CLR version 4 ou ultérieure est choisi dans le fichier de configuration, les assemblys de mode mixte créés avec des versions antérieures du .NET Framework sont chargés avec la version choisie du CLR.  La définition de cette valeur empêche la version 2.0 et la version 1.1 du CLR de se charger dans le même processus, en désactivant efficacement la fonctionnalité côte à côte in\-process.|  
|`false`|Utilisez la stratégie d'activation par défaut pour [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], qui consiste à autoriser les techniques d'activation du runtime héritées à charger le CLR version 1.1 ou 2.0 dans le processus.  La définition de cette valeur empêche le chargement d'assemblys de mode mixte dans .NET Framework 4 ou version ultérieure, sauf s'ils ont été générés avec .NET Framework 4 ou version ultérieure.  Cette valeur est celle par défaut.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Spécifie que l'application ne prend en charge que la version 1.0 du Common Language Runtime.  Les applications générées avec la version 1.1 ou ultérieure du runtime doivent utiliser l'élément **\<supportedRuntime\>**.|  
|[\<supportedRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Spécifie la version du Common Language Runtime prise en charge par l'application.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## Notes  
 L'élément **\<supportedRuntime\>** doit être utilisé par toutes les applications générées à l'aide de la version 1.1 ou ultérieure du runtime.  Les applications générées pour prendre en charge uniquement la version 1.0 du runtime doivent utiliser l'élément **\<requiredRuntime\>**.  
  
 Le code de démarrage d'une application hébergée dans Microsoft Internet Explorer ignore l'élément **\<startup\>** et ses éléments enfants.  
  
## Attribut useLegacyV2RuntimeActivationPolicy  
 Cet attribut est utile si votre application utilise des chemins d'activation hérités, comme la [fonction CorBindToRuntimeEx](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), et si vous souhaitez que ces chemins activent la version 4 du CLR au lieu d'une version antérieure, ou si votre application est générée avec [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], mais a une dépendance sur un assembly de mode mixte généré avec une version antérieure du .NET Framework.  Dans ces scénarios, affectez à l'attribut la valeur `true`.  
  
> [!NOTE]
>  L'affectation de la valeur `true` à l'attribut empêche la version 2.0 et la version 1.1 du CLR de se charger dans le même processus, en désactivant efficacement la fonctionnalité côte à côte in\-process \(consultez [Side\-by\-Side Execution for COM Interop](http://msdn.microsoft.com/fr-fr/4302318c-3586-49bf-8620-b9a39cdf4a32)\).  
  
## Exemple  
 L'exemple suivant montre comment spécifier la version du Common Language Runtime dans un fichier de configuration.  
  
```  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres de démarrage](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/fr-fr/c376208d-980d-42b4-865b-fbe0d9cc97c2)   
 [Side\-by\-Side Execution for COM Interop](http://msdn.microsoft.com/fr-fr/4302318c-3586-49bf-8620-b9a39cdf4a32)   
 [Exécution côte à côte in\-process](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)