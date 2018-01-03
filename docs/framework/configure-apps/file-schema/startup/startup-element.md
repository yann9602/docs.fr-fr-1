---
title: "&lt;démarrage&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4a502cb309bce3a1a2fb55c9e5477b7a6a395960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstartupgt-element"></a>&lt;démarrage&gt; élément
Spécifie les informations de démarrage du common language runtime.  
  
 \<configuration>  
\<démarrage >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|Attribut facultatif.<br /><br /> Spécifie s’il faut activer la [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] stratégie d’activation du runtime ou d’utiliser le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] stratégie d’activation.|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>Attribut d’useLegacyV2RuntimeActivationPolicy  
  
|Value|Description|  
|-----------|-----------------|  
|`true`|Activer [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] stratégie d’activation du runtime pour le runtime choisi, qui consiste à lier les techniques d’activation runtime hérité (telles que la [fonction CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) au runtime choisi dans le fichier de configuration au lieu de coupe les CLR version 2.0. Par conséquent, si CLR version 4 ou ultérieure est choisie dans le fichier de configuration, les assemblys en mode mixte créés avec les versions antérieures du .NET Framework sont chargées avec la version CLR choisie. Ce paramètre empêche CLR version 1.1 ou CLR version 2.0 de se charger dans le même processus, en désactivant efficacement la fonctionnalité côte à côte in-process.|  
|`false`|Utilisez la stratégie d’activation par défaut pour le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] et versions ultérieures, qui consiste à autoriser runtime hérité techniques charger le CLR version 1.1 ou 2.0 dans le processus d’activation. Ce paramètre empêche les assemblys en mode mixte de charger dans le .NET Framework 4 ou version ultérieure, sauf si elles ont été générées avec le .NET Framework 4 ou version ultérieure. Cette valeur est la valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime. Applications générées avec la version 1.1 ou ultérieure du runtime doivent utiliser le  **\<supportedRuntime >** élément.|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## <a name="remarks"></a>Notes  
 Le  **\<supportedRuntime >** élément doit être utilisé par toutes les applications générées à l’aide de la version 1.1 ou ultérieure du runtime. Les applications générées pour prendre en charge uniquement la version 1.0 du runtime doivent utiliser le  **\<requiredRuntime >** élément.  
  
 Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore la  **\<démarrage >** élément et ses éléments enfants.  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>L’attribut useLegacyV2RuntimeActivationPolicy  
 Cet attribut est utile si votre application utilise des chemins d’activation hérités, tels que les [fonction CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), et vous souhaitez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est génération avec la [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] mais a une dépendance sur un assembly en mode mixte généré avec une version antérieure du .NET Framework. Dans ces scénarios, affectez à l’attribut `true`.  
  
> [!NOTE]
>  Affectez à l’attribut `true` empêche le chargement dans le même processus, en désactivant efficacement la fonctionnalité côte à côte in-process CLR version 1.1 ou CLR version 2.0 (voir [exécution côte à côte pour COM Interop](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 [Schéma des paramètres de démarrage](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> Spécification de la version du runtime à utiliser](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [Exécution côte à côte pour COM Interop](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [Exécution côte à côte in-process](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
