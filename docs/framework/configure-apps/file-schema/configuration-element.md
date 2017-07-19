---
title: "&lt;configuration&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<configuration> (élément)"
  - "configuration (élément)"
  - "balises conteneurs, <configuration> (élément)"
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;configuration&gt;, &#233;l&#233;ment
Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.  
  
 **\<Configuration\>**  
  
## Syntaxe  
  
```  
  
      <configuration>   
   <!-- configuration settings -->   
</configuration>  
```  
  
## Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<assemblyBinding\> \(élément\)](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)|Spécifie la stratégie de liaison de l'assembly au niveau de la configuration.|  
|[Schéma des paramètres de démarrage](../../../../docs/framework/configure-apps/file-schema/startup/index.md)|Tous les éléments du schéma des paramètres de démarrage.|  
|[Schéma des paramètres d'exécution](../../../../docs/framework/configure-apps/file-schema/runtime/index.md)|Tous les éléments du schéma des paramètres d'exécution.|  
|[Schéma des paramètres de communication à distance](http://msdn.microsoft.com/fr-fr/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e)|Tous les éléments du schéma des paramètres de communication à distance.|  
|[Schéma des paramètres réseau](../../../../docs/framework/configure-apps/file-schema/network/index.md)|Tous les éléments du schéma des paramètres réseau.|  
|[Schéma des paramètres de chiffrement](../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)|Tous les éléments du schéma des paramètres de chiffrement.|  
|[Schéma des sections de configuration](../../../../docs/framework/configure-apps/file-schema/configuration-sections-schema.md)|Tous les éléments du schéma des paramètres des sections de configuration.|  
|[Schéma des paramètres de traçage et de débogage](../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)|Tous les éléments du schéma des paramètres de traçage et de débogage.|  
|[Schéma des paramètres ASP.NET](http://msdn.microsoft.com/fr-fr/116608f3-c03d-4413-9fc7-978703e18b0f)|Tous les éléments dans le schéma de configuration ASP.NET, qui inclut des éléments pour la configuration des sites Web ASP.NET et des applications.  Utilisé dans les fichiers Web.config.|  
|[Schéma des paramètres des services Web XML](http://msdn.microsoft.com/fr-fr/f84d6d55-1add-4eb7-ae46-33df5833ea2e)|Tous les éléments du schéma des paramètres des services Web.|  
|[Schéma des paramètres Web](../../../../docs/framework/configure-apps/file-schema/web/index.md)|Tous les éléments du schéma des paramètres Web, qui inclut des éléments pour la configuration d'ASP.NET en vue d'une utilisation avec une application hôte telle qu'IIS.  Utilisé dans les fichiers aspnet.config.|  
  
## Notes  
 Chaque fichier de configuration doit contenir exactement un élément **\<configuration\>**.  
  
## Voir aussi  
 [Schéma des fichiers de configuration](../../../../docs/framework/configure-apps/file-schema/index.md)