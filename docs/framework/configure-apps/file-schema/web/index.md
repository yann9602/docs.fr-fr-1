---
title: "Sch&#233;ma des param&#232;tres Web | Microsoft Docs"
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
  - "ASP.NET (système de configuration), schéma des paramètres Web"
  - "fichiers de configuration (ASP.NET)"
  - "schéma de configuration (.NET Framework), paramètres Web"
  - "paramètres Web (schéma)"
  - "paramètres Web, schéma (ASP.NET)"
  - "fichier de configuration Web.config (ASP.NET)"
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# Sch&#233;ma des param&#232;tres Web
Les paramètres Web spécifient les paramètres ASP.NET UC et d'exécution qui s'appliquent au comportement au niveau du processus géré par la couche d'hébergement ASP.NET.  Ces paramètres diffèrent des paramètres de type de domaine d'application spécifiés dans le fichier Web.config d'une application ASP.NET.  
  
 Les paramètres Web sont contenus dans les fichiers Aspnet.config situés dans les dossiers d'installation des versions du .NET Framework.  Par exemple, le fichier Aspnet.config pour [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] se trouve dans le dossier suivant :  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Les paramètres Web ne sont pas utilisés dans d'autres fichiers de configuration, tels que le fichier machine.config, le fichier Web.config racine ou les fichiers Web.config au niveau de l'application.  
  
 [\<configuration\>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<system.web\>, élément \(Paramètres Web\)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool\>, élément \(Paramètres Web\)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.web\>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Contient des informations utilisées par la couche d'hébergement d'ASP.NET.|  
|[\<applicationPool\>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Spécifie les paramètres ASP.NET UC et d'exécution qui s'appliquent au comportement au niveau du processus géré par la couche d'hébergement ASP.NET.|  
  
## Voir aussi  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)