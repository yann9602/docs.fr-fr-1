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
ms.workload: dotnet
ms.openlocfilehash: 3874a613879d099ede4968b5bce349aefa015a38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-element"></a><span data-ttu-id="8a395-102">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="8a395-102">\<configuration> element</span></span>

<span data-ttu-id="8a395-103">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a395-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="8a395-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="8a395-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8a395-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a395-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="8a395-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="8a395-106">Attributes</span></span>

<span data-ttu-id="8a395-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8a395-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="8a395-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="8a395-108">Parent element</span></span>

<span data-ttu-id="8a395-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8a395-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="8a395-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8a395-110">Child elements</span></span>

|     | <span data-ttu-id="8a395-111">Description</span><span class="sxs-lookup"><span data-stu-id="8a395-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8a395-112">**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="8a395-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="8a395-113">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="8a395-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="8a395-114">**\<démarrage >** schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="8a395-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="8a395-115">Tous les éléments dans le schéma des paramètres de démarrage.</span><span class="sxs-lookup"><span data-stu-id="8a395-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="8a395-116">**\<runtime >** schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="8a395-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="8a395-117">Tous les éléments dans le schéma de paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8a395-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="8a395-118">**\<System.Runtime.Remoting >** schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="8a395-118">**\<system.runtime.remoting>** Settings Schema</span></span>](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="8a395-119">Tous les éléments dans le schéma de paramètres de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="8a395-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="8a395-120">**\<system.Net >** schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="8a395-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="8a395-121">Tous les éléments du schéma des paramètres réseau.</span><span class="sxs-lookup"><span data-stu-id="8a395-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="8a395-122">**\<cryptographySettings >** schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="8a395-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="8a395-123">Tous les éléments du schéma des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="8a395-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="8a395-124">**\<configuration >** schéma des Sections</span><span class="sxs-lookup"><span data-stu-id="8a395-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="8a395-125">Tous les éléments dans le schéma de paramètres de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="8a395-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="8a395-126">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="8a395-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="8a395-127">Tous les éléments du schéma des paramètres de traçage et de débogage.</span><span class="sxs-lookup"><span data-stu-id="8a395-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="8a395-128">[Schéma de paramètres de Configuration ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8a395-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="8a395-129">Tous les éléments dans le schéma de configuration ASP.NET, qui inclut des éléments de configuration des applications et des sites Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8a395-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="8a395-130">Utilisé dans *Web.config* fichiers.</span><span class="sxs-lookup"><span data-stu-id="8a395-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="8a395-131">**\<webServices >** schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="8a395-131">**\<webServices>** Settings Schema</span></span>](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="8a395-132">Tous les éléments du schéma des paramètres Web services.</span><span class="sxs-lookup"><span data-stu-id="8a395-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="8a395-133">Schéma des paramètres web</span><span class="sxs-lookup"><span data-stu-id="8a395-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="8a395-134">Tous les éléments du schéma des paramètres Web, qui inclut des éléments pour la configuration d'ASP.NET en vue d'une utilisation avec une application hôte telle qu'IIS.</span><span class="sxs-lookup"><span data-stu-id="8a395-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="8a395-135">Utilisé dans *aspnet.config* fichiers.</span><span class="sxs-lookup"><span data-stu-id="8a395-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8a395-136">Notes</span><span class="sxs-lookup"><span data-stu-id="8a395-136">Remarks</span></span>

<span data-ttu-id="8a395-137">Chaque fichier de configuration doit contenir exactement un  **\<configuration >** élément.</span><span class="sxs-lookup"><span data-stu-id="8a395-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a395-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a395-138">See also</span></span>

[<span data-ttu-id="8a395-139">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a395-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
