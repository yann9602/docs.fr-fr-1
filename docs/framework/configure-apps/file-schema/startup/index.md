---
title: "Sch&#233;ma des param&#232;tres de d&#233;marrage | Microsoft Docs"
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
  - "schéma de configuration (.NET Framework), paramètres de démarrage"
  - "paramètres de démarrage (schéma)"
  - "schéma des paramètres de démarrage"
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Sch&#233;ma des param&#232;tres de d&#233;marrage
Les paramètres de démarrage spécifient la version du Common Language Runtime qui doit exécuter l'application.  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Spécifie que l'application ne prend en charge que la version 1.0 du Common Language Runtime.  Les applications générées avec la version 1.1 du runtime doivent utiliser l'élément **\<supportedRuntime\>**.|  
|[\<supportedRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Spécifie la version du Common Language Runtime prise en charge par l'application.|  
|[\<démarrage\>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Contient les éléments **\<requiredRuntime\>** et **\<supportedRuntime\>**.|  
  
## Voir aussi  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/fr-fr/c376208d-980d-42b4-865b-fbe0d9cc97c2)