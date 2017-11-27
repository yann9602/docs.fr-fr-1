---
title: "Schéma des fichiers de configuration pour le .NET Framework"
ms.custom: 
ms.date: 05/01/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7f2dec0d71c1a0822bf39ae420d4e56bdaf99e0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Schéma des fichiers de configuration pour le .NET Framework

Les fichiers de configuration sont des fichiers XML standard que vous pouvez utiliser pour modifier les paramètres et définir des stratégies pour vos applications. Le schéma de configuration .NET Framework se compose d'éléments que vous pouvez utiliser dans les fichiers de configuration pour contrôler le comportement de vos applications. La table des matières de cette section reflète la hiérarchie du schéma pour les paramètres de démarrage, de runtime et de réseau, ainsi que pour d'autres types de paramètres de configuration.

Pour plus d’informations sur les types, le format et l’emplacement des fichiers de configuration, consultez l’article [Configuration d’applications](~/docs/framework/configure-apps/index.md). Familiarisez-vous avec le langage XML si vous souhaitez modifier directement les fichiers de configuration.

> [!IMPORTANT]
> Les étiquettes et attributs XML des fichiers de configuration respectent la casse.

## <a name="in-this-section"></a>Dans cette section

[**\<configuration>**, élément](~/docs/framework/configure-apps/file-schema/configuration-element.md) Décrit l’élément `<configuration>`, qui constitue l’élément de niveau supérieur de tous les fichiers de configuration.

[**\<assemblyBinding>**, élément](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.

[**\<linkedConfiguration>**, élément](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Spécifie un fichier de configuration à inclure.

[Schéma des paramètres de démarrage](~/docs/framework/configure-apps/file-schema/startup/index.md) Décrit les éléments qui spécifient la version du common language runtime à utiliser.

[Schéma des paramètres d’exécution](~/docs/framework/configure-apps/file-schema/runtime/index.md) Décrit les éléments qui configurent les liaisons d’assembly et le comportement au moment de l’exécution.

[Schéma des paramètres réseau](~/docs/framework/configure-apps/file-schema/network/index.md) Décrit les éléments qui spécifient la manière dont le .NET Framework se connecte à Internet.

[Schéma des paramètres de chiffrement](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Décrit des éléments qui mappent des noms d’algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.

[Schéma des sections de configuration](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Décrit les éléments qui servent à créer et à utiliser les sections de configuration pour les paramètres personnalisés.

[Schéma des paramètres de traçage et de débogage](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Décrit les éléments qui spécifient les commutateurs et les écouteurs de traçage.

[Schéma des paramètres du fournisseur de langage et du compilateur](~/docs/framework/configure-apps/file-schema/compiler/index.md) Décrit les éléments qui spécifient la configuration de compilateur pour les fournisseurs de langages disponibles.

[Schéma des paramètres d’application](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Décrit les éléments qui permettent à une application Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.

[Schéma des paramètres d’application](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contient des paramètres d’application personnalisés, tels que des chemins de fichier, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.

[Schéma des paramètres web](~/docs/framework/configure-apps/file-schema/web/index.md) Tous les éléments du schéma des paramètres web, qui inclut des éléments pour la configuration d’ASP.NET en vue d’une utilisation avec une application hôte telle qu’IIS. Utilisé dans les fichiers *Aspnet.config*.

[Schéma de configuration Windows Forms](winforms/index.md) Tous les éléments de la section de configuration d’application Windows Forms, qui inclut les personnalisations telles que de la prise en charge de plusieurs moniteurs et de la haute résolution.

[Schéma de configuration WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) Tous les éléments qui vous permettent de configurer les applications clientes et le service WCF.

[Syntaxe de directive WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Décrit la directive `@ServiceHost`, qui définit des attributs spécifiques de la page utilisés par le compilateur .svc.

[Schéma de configuration WIF](windows-identity-foundation/index.md) Tous les éléments du schéma de configuration Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Rubriques connexes

[Schéma des paramètres de communication à distance](http://msdn.microsoft.com/en-us/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Décrit les éléments qui configurent les applications clientes et serveur qui implémentent la communication à distance.

[Schéma de paramètres ASP.NET](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Décrit les éléments qui contrôlent le comportement des applications web ASP.NET.

[Schéma des paramètres des services Web](http://msdn.microsoft.com/en-us/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Décrit les éléments qui contrôlent le comportement des services web ASP.NET et de leurs clients.

[Configuration d’applications .NET Framework](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Décrit comment configurer la sécurité, les liaisons d’assembly et la communication à distance dans le .NET Framework.
