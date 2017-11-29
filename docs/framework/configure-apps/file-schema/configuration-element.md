---
title: "&lt;configuration&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2241f3e835defe308b94d0cbad96020518dfd19b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-element"></a>\<configuration > élément

Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.

**\<configuration>**

## <a name="syntax"></a>Syntaxe

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>Attributs

Aucune

## <a name="parent-element"></a>Élément parent

Aucune

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.|
| [**\<démarrage >** schéma des paramètres](~/docs/framework/configure-apps/file-schema/startup/index.md) | Tous les éléments dans le schéma des paramètres de démarrage. |
| [**\<runtime >** schéma des paramètres](~/docs/framework/configure-apps/file-schema/runtime/index.md) | Tous les éléments dans le schéma de paramètres d’exécution. |
| [**\<System.Runtime.Remoting >** schéma des paramètres](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | Tous les éléments dans le schéma de paramètres de communication à distance. |
| [**\<system.Net >** schéma des paramètres](~/docs/framework/configure-apps/file-schema/network/index.md) | Tous les éléments du schéma des paramètres réseau. |
| [**\<cryptographySettings >** schéma des paramètres](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | Tous les éléments du schéma des paramètres de chiffrement. |
| [**\<configuration >** schéma des Sections](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | Tous les éléments dans le schéma de paramètres de section de configuration. |
| [Schéma des paramètres de trace et de débogage](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | Tous les éléments du schéma des paramètres de traçage et de débogage. |
| [Schéma de paramètres de Configuration ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx) | Tous les éléments dans le schéma de configuration ASP.NET, qui inclut des éléments de configuration des applications et des sites Web ASP.NET. Utilisé dans *Web.config* fichiers. |
| [**\<webServices >** schéma des paramètres](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | Tous les éléments du schéma des paramètres Web services. |
| [Schéma des paramètres web](~/docs/framework/configure-apps/file-schema/web/index.md) | Tous les éléments du schéma des paramètres Web, qui inclut des éléments pour la configuration d'ASP.NET en vue d'une utilisation avec une application hôte telle qu'IIS. Utilisé dans *aspnet.config* fichiers. |

## <a name="remarks"></a>Remarques

Chaque fichier de configuration doit contenir exactement un  **\<configuration >** élément.

## <a name="see-also"></a>Voir aussi

[Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
