---
title: "&lt;appDomainManagerType&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "<appDomainManagerType> (élément)"
  - "appDomainManagerType (élément)"
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;appDomainManagerType&gt;, &#233;l&#233;ment
Spécifie le type qui sert de gestionnaire de domaine d'application pour le domaine d'application par défaut.  
  
## Syntaxe  
  
```  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`value`|Attribut requis.  Spécifie le nom du type, notamment l'espace de noms, qui sert de gestionnaire de domaine d'application pour le domaine d'application par défaut dans le processus.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d'assembly et l'opération garbage collection.|  
  
## Notes  
 Pour spécifier le type du gestionnaire de domaine d'application, vous devez indiquer cet élément et l'élément [\<appDomainManagerAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) .  Si l'un de ces éléments n'est pas spécifié, l'autre est ignoré.  
  
 Lorsque le domaine d'application par défaut est chargé, <xref:System.TypeLoadException> est levée si le type spécifié n'existe pas dans l'assembly indiqué par l'élément [\<appDomainManagerAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md), et le processus ne peut pas démarrer.  
  
 Lorsque vous spécifiez le type du gestionnaire de domaine d'application pour le domaine d'application par défaut, d'autres domaines d'application créés à partir du domaine d'application par défaut héritent du type du gestionnaire de domaine d'application.  Utilisez les propriétés <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=fullName> et <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=fullName> afin de spécifier un type de gestionnaire de domaine d'application différent pour un nouveau domaine d'application.  
  
 La spécification du type du gestionnaire de domaine d'application requiert que l'application dispose d'une confiance totale. \(C'est le cas, par exemple, d'une application qui s'exécute sur le Bureau.\) Si l'application ne dispose pas d'une confiance totale, une <xref:System.TypeLoadException> est levée.  
  
 Le format du type et de l'espace de noms est le même que celui utilisé pour la propriété <xref:System.Type.FullName%2A?displayProperty=fullName>.  
  
 Cet élément de configuration est disponible uniquement dans le [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] et versions ultérieures.  
  
## Exemple  
 L'exemple suivant indique comment spécifier que le gestionnaire de domaine d'application pour le domaine d'application par défaut d'un processus est le type `MyMgr` dans l'assembly `AdMgrExample`.  
  
```  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=fullName>   
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=fullName>   
 [\<appDomainManagerAssembly\>, élément](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)   
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [SetAppDomainManagerType, méthode](../Topic/ICLRControl::SetAppDomainManagerType%20Method.md)