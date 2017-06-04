---
title: "&lt;disableFusionUpdatesFromADManager&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<disableFusionUpdatesFromADManager> (élément)"
  - "disableFusionUpdatesFromADManager (élément)"
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;disableFusionUpdatesFromADManager&gt;, &#233;l&#233;ment
Spécifie si le comportement par défaut, qui consiste à autoriser l'hôte du runtime à substituer les paramètres de configuration pour un domaine d'application, est désactivé.  
  
## Syntaxe  
  
```  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|activé|Attribut requis.<br /><br /> Spécifie si la possibilité par défaut de substituer des paramètres Fusion est désactivée.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|0|Ne désactivez pas la possibilité de substituer des paramètres Fusion.  Il s'agit du comportement par défaut depuis le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Désactivez la possibilité de substituer des paramètres Fusion.  Cela rétablit le comportement des versions antérieures du .NET Framework.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Depuis le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], le comportement par défaut consiste à autoriser l'objet <xref:System.AppDomainManager> à substituer des paramètres de configuration à l'aide de la propriété <xref:System.AppDomainSetup.ConfigurationFile%2A> ou de la méthode <xref:System.AppDomainSetup.SetConfigurationBytes%2A> de l'objet <xref:System.AppDomainSetup> qui est passé à votre implémentation de la méthode <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=fullName>, dans votre sous\-classe de <xref:System.AppDomainManager>.  Pour le domaine d'application par défaut, les paramètres que vous modifiez substituent ceux spécifiés par le fichier de configuration de l'application.  Pour d'autres domaines d'application, ils substituent les paramètres de configuration passés à la méthode <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=fullName> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=fullName>.  
  
 Vous pouvez passer de nouvelles informations de configuration ou passer null \(`Nothing` en Visual Basic\) afin d'éliminer les informations de configuration passées.  
  
 Ne passez pas d'informations de configuration à la fois à la propriété <xref:System.AppDomainSetup.ConfigurationFile%2A> et à la méthode <xref:System.AppDomainSetup.SetConfigurationBytes%2A>.  Sinon, les informations que vous passez à la propriété <xref:System.AppDomainSetup.ConfigurationFile%2A> sont ignorées, car la méthode <xref:System.AppDomainSetup.SetConfigurationBytes%2A> substitue les informations de configuration dans le fichier de configuration de l'application.  Si vous utilisez la propriété <xref:System.AppDomainSetup.ConfigurationFile%2A>, vous pouvez passer null \(`Nothing` en Visual Basic\) à la méthode <xref:System.AppDomainSetup.SetConfigurationBytes%2A> pour éliminer les octets de configuration spécifiés dans l'appel à la méthode <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=fullName> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=fullName>.  
  
 Outre les informations de configuration, vous pouvez modifier les paramètres suivants sur l'objet <xref:System.AppDomainSetup> passé à votre implémentation de la méthode <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=fullName> : <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> et <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Comme alternative à l'utilisation de l'élément `<disableFusionUpdatesFromADManager>`, vous pouvez désactiver le comportement par défaut en créant un paramètre du Registre ou en définissant une variable d'environnement.  Dans le Registre, créez une valeur DWORD nommée `COMPLUS_disableFusionUpdatesFromADManager` sous `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework` et affectez\-lui la valeur 1.  Depuis la ligne de commande, affectez à la variable d'environnement `COMPLUS_disableFusionUpdatesFromADManager` la valeur 1.  
  
## Exemple  
 L'exemple de code suivant indique comment désactiver la possibilité de substituer des paramètres Fusion à l'aide de l'élément `<disableFusionUpdatesFromADManager>`.  
  
```  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Méthode de localisation des assemblys par le runtime](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)