---
title: "&lt;NetFx40_LegacySecurityPolicy&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<NetFx40_LegacySecurityPolicy> (élément)"
  - "NetFx40_LegacySecurityPolicy (élément)"
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;NetFx40_LegacySecurityPolicy&gt;, &#233;l&#233;ment
Spécifie si le runtime utilise la stratégie de sécurité d'accès du code héritée \(legacy\) \(CAS, Code Access Security\).  
  
## Syntaxe  
  
```  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime utilise la stratégie de sécurité d'accès du code héritée \(legacy\).|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Le runtime n'utilise pas la stratégie de sécurité d'accès du code héritée.  Il s'agit de la valeur par défaut.|  
|`true`|Le runtime utilise la stratégie de sécurité d'accès du code héritée.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
 Dans le .NET Framework version 3.5 et versions antérieures, la stratégie CAS est toujours appliquée.  Dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], la stratégie CAS doit être activée.  
  
 La stratégie CAS est spécifique à la version.  Les stratégies CAS personnalisées qui existent dans les versions antérieures du .NET Framework doivent être de nouveau spécifiées dans le [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 L'application de l'élément `<NetFx40_LegacySecurityPolicy>` à un assembly [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] n'affecte pas le [code transparent de sécurité](../../../../../docs/framework/misc/security-transparent-code.md); les règles de transparence s'appliquent encore.  
  
> [!IMPORTANT]
>  L'application de l'élément `<NetFx40_LegacySecurityPolicy>` peut provoquer des altérations des performances significatives pour les assemblys d'image natifs créés par le [Générateur d'image natif \(Ngen.exe\)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) qui ne sont pas installés dans le [Global Assembly Cache](../../../../../docs/framework/app-domains/gac.md).  La dégradation des performances est causée par l'incapacité de l'exécution à charger les assemblys comme images natives lorsque l'attribut est appliqué, ce qui provoque leur chargement comme assemblys juste\-à\-temps.  
  
> [!NOTE]
>  Si vous spécifiez une version du .NET Framework cible antérieure au [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] dans les paramètres du projet pour votre projet Visual Studio, la stratégie CAS sera activée, avec toutes les stratégies CAS personnalisées que vous avez spécifiées pour cette version.  Toutefois, vous ne serez pas en mesure d'utiliser les nouveaux types et membres [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  Vous pouvez également spécifier une version antérieure du .NET Framework à l'aide de l'élément [\<supportedRuntime\> .](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) du schéma de paramètres de démarrage de votre [fichier de configuration d'application](../../../../../docs/framework/configure-apps/index.md).  
  
> [!NOTE]
>  La syntaxe des fichiers de configuration respecte la casse.  Vous devez utiliser la syntaxe fournie dans les sections Syntaxe et Exemple.  
  
## Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant montre comment activer la stratégie de sécurité d'accès du code héritée \(legacy\) d'une application.  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)