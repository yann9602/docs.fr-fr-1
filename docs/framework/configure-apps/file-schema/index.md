---
title: "Sch&#233;ma des fichiers de configuration pour le .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "configuration d'applications .NET Framework, schéma de configuration"
  - "fichiers app.config, schéma"
  - "fichiers de configuration de l'application, schéma"
  - "développement d'applications (.NET Framework), schéma"
  - "schéma de configuration (.NET Framework)"
  - "paramètres de configuration (.NET Framework), applications"
  - "balises conteneurs"
  - "fichiers de configuration enterprisesec"
  - "fichiers enterprisesec.config"
  - "fichiers de configuration machine"
  - "fichiers machine.config"
  - "paramètres de configuration (schéma)"
  - "schémas, paramètres de configuration"
  - "sécurité (.NET Framework), fichiers de configuration"
  - "fichiers security.config"
  - "XML bien formé"
  - "balises XML"
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# Sch&#233;ma des fichiers de configuration pour le .NET Framework
Les fichiers de configuration sont des fichiers XML standard que vous pouvez utiliser pour modifier les paramètres et définir des stratégies pour vos applications.  Le schéma de configuration .NET Framework se compose d'éléments que vous pouvez utiliser dans les fichiers de configuration pour contrôler le comportement de vos applications.  La table des matières de cette section reflète la hiérarchie du schéma pour les paramètres de démarrage, de runtime et de réseau, ainsi que pour d'autres types de paramètres de configuration.  
  
 Pour plus d'informations sur les types, le format et l'emplacement des fichiers de configuration, consultez l'article [Configuration d'applications](../../../../docs/framework/configure-apps/index.md).  Vous devez bien connaître le langage XML si vous souhaitez modifier directement les fichiers de configuration.  
  
> [!IMPORTANT]
>  Les balises et attributs XML des fichiers de configuration respectent la casse.  
  
## Dans cette section  
 [\<configuration\>, élément](../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
 Décrit l'élément `<configuration>`, qui constitue l'élément de niveau supérieur de tous les fichiers de configuration.  
  
 [\<assemblyBinding\> \(élément\)](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)  
 Spécifie la stratégie de liaison de l'assembly au niveau de la configuration.  
  
 [\<linkedConfiguration\> \(élément\)](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)  
 Spécifie un fichier de configuration à inclure.  
  
 [Schéma des paramètres de démarrage](../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 Décrit les éléments qui spécifient la version du Common Language Runtime à utiliser.  
  
 [Schéma des paramètres d'exécution](../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 Décrit les éléments qui configurent les liaisons d'assembly et comportement au moment de l'exécution.  
  
 [Schéma des paramètres réseau](../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 Décrit les éléments qui spécifient la manière dont le .NET Framework se connecte à Internet.  
  
 [Schéma des paramètres de chiffrement](../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 Décrit des éléments qui mappent des noms d'algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.  
  
 [Schéma des sections de configuration](../../../../docs/framework/configure-apps/file-schema/configuration-sections-schema.md)  
 Décrit les éléments qui servent à créer et à utiliser les sections de configuration pour les paramètres personnalisés.  
  
 [Schéma des paramètres de traçage et de débogage](../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 Décrit les éléments qui spécifient les commutateurs et les écouteurs de traçage.  
  
 [Schéma des paramètres du fournisseur de langage et du compilateur](../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 Décrit les éléments qui spécifient la configuration de compilateur pour les fournisseurs de langages disponibles.  
  
 [Schéma des paramètres d'application](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)  
 Décrit les éléments qui permettent à une application Windows Forms ou ASP.NET de stocker et d'extraire des paramètres de portée application et de portée utilisateur.  
  
 [Schéma des paramètres Web](../../../../docs/framework/configure-apps/file-schema/web/index.md)  
 Tous les éléments du schéma des paramètres Web, qui inclut des éléments pour la configuration d'ASP.NET en vue d'une utilisation avec une application hôte telle qu'IIS.  Utilisé dans les fichiers aspnet.config.  
  
## Rubriques connexes  
 [Remoting Settings Schema](http://msdn.microsoft.com/fr-fr/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e)  
 Décrit les éléments qui configurent les applications client\-serveur qui implémentent la communication à distance.  
  
 [Schéma des paramètres ASP.NET](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx)  
 Décrit les éléments qui contrôlent le comportement d'applications web ASP.NET.  
  
 [Web Services Settings Schema](http://msdn.microsoft.com/fr-fr/f84d6d55-1add-4eb7-ae46-33df5833ea2e)  
 Décrit les éléments qui contrôlent le comportement des services web ASP.NET et de leurs clients.  
  
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/fr-fr/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 Décrit comment configurer la sécurité, les liaisons d'assembly et la communication à distance dans le .NET Framework.