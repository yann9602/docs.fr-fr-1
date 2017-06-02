---
title: "&lt;supportedRuntime&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<supportedRuntime> (élément)"
  - "supportedRuntime (élément)"
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
caps.latest.revision: 33
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 28
---
# &lt;supportedRuntime&gt;, &#233;l&#233;ment
Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application. Cet élément doit être utilisé par toutes les applications créées avec la version 1.1 ou ultérieure du .NET Framework.  
  
 [\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<startup\>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
  
 **\<supportedRuntime\>**  
  
## Syntaxe  
  
```  
  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**version**|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la version du Common Language Runtime \(CLR\) prise en charge par cette application. Pour les valeurs valides de l’attribut `version`, consultez la section [valeurs de "runtime version"](#version). **Note:**  Dans le .NET Framework 3.5, la valeur de "*runtime version*" prend la forme *majeure*.*mineure*.*build*. Depuis [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], seuls les numéros de version principale et secondaire sont nécessaires \(c'est\-à\-dire "v4.0" au lieu de "v4.0.30319"\). La chaîne courte est recommandée.|  
|**référence**|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la référence \(SKU\), qui à son tour spécifie quelle version du .NET Framework cette application prend en charge.<br /><br /> À compter du .NET Framework 4.0, l’utilisation de l’attribut `sku` est recommandée.  Quand il est présent, il indique la version du .NET Framework ciblée par l’application.<br /><br /> Pour les valeurs valides de l’attribut sku, consultez la section [valeurs de "sku id"](#sku).|  
  
## Notes  
 Si l'élément **\<supportedRuntime\>** n'est pas dans le fichier de configuration de l'application, la version du runtime utilisée pour générer l'application est utilisée.  
  
 L'élément **\<supportedRuntime\>** doit être utilisé par toutes les applications générées à l'aide de la version 1.1 du runtime ou ultérieure. Les applications générées pour prendre en charge uniquement la version 1.0 du runtime doivent utiliser l'élément [\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md).  
  
> [!NOTE]
>  Si vous utilisez la fonction [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) pour spécifier le fichier de configuration, vous devez employer l'élément `<requiredRuntime>` pour toutes les versions du runtime. L'élément `<supportedRuntime>` est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 Pour les applications prenant en charge les versions du runtime du .NET Framework 1.1 à 3.5, quand plusieurs versions du runtime sont prises en charge, le premier élément doit spécifier la version du runtime préférée en premier tandis que le dernier élément doit spécifier la version préférée en dernier. Pour les applications prenant en charge le .NET Framework 4.0 ou ultérieur, l’attribut `version` indique la version du CLR, qui est commune au .NET Framework 4 et aux versions ultérieures tandis que l’attribut `sku` indique la seule version du .NET Framework ciblée par l’application.  
  
> [!NOTE]
>  Si votre application utilise des chemins d'activation hérités, tels que la [fonction CorBindToRuntimeEx](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), et si vous souhaitez que ces chemins activent la version 4 du CLR plutôt qu'une version antérieure, ou si votre application est générée avec [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], mais a une dépendance sur un assembly de mode mixte généré avec une version antérieure du .NET Framework, il ne suffit pas de spécifier [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] dans la liste des runtimes pris en charge. De plus, dans l'[élément \<startup\>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) de votre fichier de configuration, vous devez affecter à l'attribut `useLegacyV2RuntimeActivationPolicy` la valeur `true`. Toutefois, l'affectation de la valeur `true` à cet attribut signifie que tous les composants générés avec des versions antérieures du .NET Framework sont exécutés à l'aide de [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] plutôt qu'à l'aide des runtimes avec lesquels ils ont été générés.  
  
 Nous vous recommandons de tester les applications avec toutes les versions du .NET Framework sur lesquelles elles peuvent s'exécuter.  
  
<a name="version"></a>   
## valeurs de "runtime version"  
 Le tableau suivant répertorie les valeurs valides pour *runtime version* de l’attribut `version`.  
  
|Version du .NET Framework|Attribut `version`|  
|-------------------------------|------------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2.0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0|"v4.0"|  
|4.5|"v4.0"|  
|4.5.1|"v4.0"|  
|4.5.2|"v4.0"|  
|4.6|"v4.0"|  
|4.6.1|"v4.0"|  
  
<a name="sku"></a>   
## valeurs de "sku id"  
 Le tableau suivant répertorie les versions du .NET Framework qui sont prises en charge par l’attribut `sku` depuis le .NET Framework 4.  Notez que l’attribut `sku` indique la version du .NET Framework ciblée par l’application depuis le .NET Framework 4.  
  
|Version du .NET Framework|Attribut `sku`|  
|-------------------------------|--------------------|  
|4.0|".NETFramework,Version\=v4.0"|  
|4.0, Client Profile|".NETFramework,Version\=v4.0,Profile\=Client"|  
|4.0, Platform Update 1|.NETFramework,Version\=v4.0.1|  
|4.0, Client Profile, Update 1|.NETFramework, Version\=v4.0.1, Profile\=Client|  
|4.0, Platform Update 2|.NETFramework,Version\=v4.0.2|  
|4.0, Client Profile, Update 2|.NETFramework, Version\=v4.0.2, Profile\=Client|  
|4.0, Platform Update 3|.NETFramework,Version\=v4.0.3|  
|4.0, Client Profile, Update 3|.NETFramework, Version\=v4.0.3, Profile\=Client|  
|4.5|".NETFramework,Version\=v4.5"|  
|4.5.1|".NETFramework,Version\=v4.5.1"|  
|4.5.2|".NETFramework,Version\=v4.5.2"|  
|4.6|".NETFramework,Version\=v4.6"|  
|4.6.1|".NETFramework,Version\=v4.6.1"|  
  
 Le tableau suivant indique sur quelles versions du .NET Framework 4 une application s’exécute, pour différentes valeurs de l’attribut `sku`, quand l’attribut `version` est v4.0 et l’attribut `sku` identifie le .NET Framework 4 ou une de ses mises à jour de plateforme \(PU\).  
  
|Valeur de l'attribut `sku`|4.0 version de client|4.0 version complète|4.0 version de client \+ PU 1|4.0 version complète \+ PU 1|4.0 version de client \+ PU 2|4.0 version complète \+ PU 2|4.0 version de client \+ PU 3|4.0 version complète \+ PU 3|4.5 et ultérieure|  
|--------------------------------|---------------------------|--------------------------|-----------------------------------|----------------------------------|-----------------------------------|----------------------------------|-----------------------------------|----------------------------------|-----------------------|  
|.NETFramework, Version\=v4.0, Profile\=Client|Oui|Oui|Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|.NETFramework,Version\=v4.0||Oui||Oui||Oui||Oui|Oui|  
|.NETFramework, Version\=v4.0.1, Profile\=Client|||Oui|Oui|Oui|Oui|Oui|Oui|Oui|  
|.NETFramework,Version\=v4.0.1||||Oui||Oui||Oui|Oui|  
|.NETFramework, Version\=v4.0.2, Profile\=Client|||||Oui|Oui|Oui|Oui|Oui|  
|.NETFramework,Version\=v4.0.2||||||Oui||Oui|Oui|  
|.NETFramework, Version\=v4.0.3, Profile\=Client|||||||Oui|Oui|Oui|  
|.NETFramework,Version\=v4.0.3||||||||Oui|Oui|  
  
## Exemple  
 L’exemple suivant montre comment spécifier la version du runtime prise en charge dans un fichier de configuration. Le fichier de configuration indique que l’application cible le .NET Framework 4.6.  
  
```xml  
  
<configuration> <startup> <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" /> </startup> </configuration>  
  
```  
  
## Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'application.  
  
## Voir aussi  
 [Schéma des paramètres de démarrage](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Spécification de la version du runtime à utiliser](http://msdn.microsoft.com/fr-fr/c376208d-980d-42b4-865b-fbe0d9cc97c2)   
 [Exécution côte à côte in\-process](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)