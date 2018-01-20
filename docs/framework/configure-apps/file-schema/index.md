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
ms.workload: dotnet
ms.openlocfilehash: 4af28280de24f3e25362f18985c209b1a2f29523
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="8c956-102">Schéma des fichiers de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c956-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="8c956-103">Les fichiers de configuration sont des fichiers XML standard que vous pouvez utiliser pour modifier les paramètres et définir des stratégies pour vos applications.</span><span class="sxs-lookup"><span data-stu-id="8c956-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="8c956-104">Le schéma de configuration .NET Framework se compose d'éléments que vous pouvez utiliser dans les fichiers de configuration pour contrôler le comportement de vos applications.</span><span class="sxs-lookup"><span data-stu-id="8c956-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="8c956-105">La table des matières de cette section reflète la hiérarchie du schéma pour les paramètres de démarrage, de runtime et de réseau, ainsi que pour d'autres types de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="8c956-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="8c956-106">Pour plus d’informations sur les types, le format et l’emplacement des fichiers de configuration, consultez l’article [Configuration d’applications](~/docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c956-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](~/docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="8c956-107">Familiarisez-vous avec le langage XML si vous souhaitez modifier directement les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="8c956-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c956-108">Les étiquettes et attributs XML des fichiers de configuration respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="8c956-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8c956-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8c956-109">In this section</span></span>

<span data-ttu-id="8c956-110">[**\<configuration>**, élément](~/docs/framework/configure-apps/file-schema/configuration-element.md) Décrit l’élément `<configuration>`, qui constitue l’élément de niveau supérieur de tous les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="8c956-110">[**\<configuration>** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="8c956-111">[**\<assemblyBinding>**, élément](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="8c956-111">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="8c956-112">[**\<linkedConfiguration>**, élément](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Spécifie un fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="8c956-112">[**\<linkedConfiguration>** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="8c956-113">[Schéma des paramètres de démarrage](~/docs/framework/configure-apps/file-schema/startup/index.md) Décrit les éléments qui spécifient la version du common language runtime à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8c956-113">[Startup Settings Schema](~/docs/framework/configure-apps/file-schema/startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="8c956-114">[Schéma des paramètres d’exécution](~/docs/framework/configure-apps/file-schema/runtime/index.md) Décrit les éléments qui configurent les liaisons d’assembly et le comportement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8c956-114">[Runtime Settings Schema](~/docs/framework/configure-apps/file-schema/runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="8c956-115">[Schéma des paramètres réseau](~/docs/framework/configure-apps/file-schema/network/index.md) Décrit les éléments qui spécifient la manière dont le .NET Framework se connecte à Internet.</span><span class="sxs-lookup"><span data-stu-id="8c956-115">[Network Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="8c956-116">[Schéma des paramètres de chiffrement](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Décrit des éléments qui mappent des noms d’algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="8c956-116">[Cryptography Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="8c956-117">[Schéma des sections de configuration](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Décrit les éléments qui servent à créer et à utiliser les sections de configuration pour les paramètres personnalisés.</span><span class="sxs-lookup"><span data-stu-id="8c956-117">[Configuration Sections Schema](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="8c956-118">[Schéma des paramètres de traçage et de débogage](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Décrit les éléments qui spécifient les commutateurs et les écouteurs de traçage.</span><span class="sxs-lookup"><span data-stu-id="8c956-118">[Trace and Debug Settings Schema](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="8c956-119">[Schéma des paramètres du fournisseur de langage et du compilateur](~/docs/framework/configure-apps/file-schema/compiler/index.md) Décrit les éléments qui spécifient la configuration de compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="8c956-119">[Compiler and Language Provider Settings Schema](~/docs/framework/configure-apps/file-schema/compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="8c956-120">[Schéma des paramètres d’application](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Décrit les éléments qui permettent à une application Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8c956-120">[Application Settings Schema](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="8c956-121">[Schéma des paramètres d’application](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contient des paramètres d’application personnalisés, tels que des chemins de fichier, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="8c956-121">[App Settings Schema](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="8c956-122">[Schéma des paramètres web](~/docs/framework/configure-apps/file-schema/web/index.md) Tous les éléments du schéma des paramètres web, qui inclut des éléments pour la configuration d’ASP.NET en vue d’une utilisation avec une application hôte telle qu’IIS.</span><span class="sxs-lookup"><span data-stu-id="8c956-122">[Web Settings Schema](~/docs/framework/configure-apps/file-schema/web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="8c956-123">Utilisé dans les fichiers *Aspnet.config*.</span><span class="sxs-lookup"><span data-stu-id="8c956-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="8c956-124">[Schéma de configuration Windows Forms](winforms/index.md) Tous les éléments de la section de configuration d’application Windows Forms, qui inclut les personnalisations telles que de la prise en charge de plusieurs moniteurs et de la haute résolution.</span><span class="sxs-lookup"><span data-stu-id="8c956-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="8c956-125">[Schéma de configuration WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) Tous les éléments qui vous permettent de configurer les applications clientes et le service WCF.</span><span class="sxs-lookup"><span data-stu-id="8c956-125">[WCF Configuration Schema](~/docs/framework/configure-apps/file-schema/wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="8c956-126">[Syntaxe de directive WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Décrit la directive `@ServiceHost`, qui définit des attributs spécifiques de la page utilisés par le compilateur .svc.</span><span class="sxs-lookup"><span data-stu-id="8c956-126">[WCF Directive Syntax](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="8c956-127">[Schéma de configuration WIF](windows-identity-foundation/index.md) Tous les éléments du schéma de configuration Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="8c956-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8c956-128">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8c956-128">Related sections</span></span>

<span data-ttu-id="8c956-129">[Schéma des paramètres de communication à distance](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Décrit les éléments qui configurent les applications clientes et serveur qui implémentent la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="8c956-129">[Remoting Settings Schema](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="8c956-130">[Schéma de paramètres ASP.NET](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Décrit les éléments qui contrôlent le comportement des applications web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8c956-130">[ASP.NET Settings Schema](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="8c956-131">[Schéma des paramètres des services Web](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Décrit les éléments qui contrôlent le comportement des services web ASP.NET et de leurs clients.</span><span class="sxs-lookup"><span data-stu-id="8c956-131">[Web Services Settings Schema](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="8c956-132">[Configuration d’applications .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Décrit comment configurer la sécurité, les liaisons d’assembly et la communication à distance dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c956-132">[Configuring .NET Framework Apps](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
