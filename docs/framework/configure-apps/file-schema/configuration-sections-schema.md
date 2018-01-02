---
title: "Schéma des sections de configuration"
ms.date: 05/02/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da9af8fd24f1bf6e6effd411ad37490a4ee08804
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="1f6cd-102">Schéma des sections de configuration</span><span class="sxs-lookup"><span data-stu-id="1f6cd-102">Configuration sections schema</span></span>

<span data-ttu-id="1f6cd-103">Le schéma des sections de configuration contient des éléments qui définissent les paramètres personnalisés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="1f6cd-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="1f6cd-104">Pour obtenir des informations générales sur les schémas et les fichiers de configuration, consultez [schéma de fichier de Configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f6cd-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="1f6cd-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1f6cd-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="1f6cd-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="1f6cd-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="1f6cd-107">[**\<Désactivez >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="1f6cd-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="1f6cd-108">[**\<Supprimer >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="1f6cd-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="1f6cd-109">[**\<section >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="1f6cd-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="1f6cd-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="1f6cd-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="1f6cd-111">Description</span><span class="sxs-lookup"><span data-stu-id="1f6cd-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1f6cd-112">**\<Désactivez >** pour  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="1f6cd-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="1f6cd-113">Efface toutes les sections précédemment définies et des groupes.</span><span class="sxs-lookup"><span data-stu-id="1f6cd-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="1f6cd-114">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="1f6cd-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="1f6cd-115">Efface toutes les sections précédemment définies et des groupes.</span><span class="sxs-lookup"><span data-stu-id="1f6cd-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="1f6cd-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="1f6cd-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="1f6cd-117">Contient des déclarations d’espace de noms et de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="1f6cd-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="1f6cd-118">**\<Supprimer >** pour  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="1f6cd-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="1f6cd-119">Supprime un groupe de sections ou une section prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="1f6cd-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="1f6cd-120">**\<section >** pour  **\<configSections >** et  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="1f6cd-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="1f6cd-121">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="1f6cd-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="1f6cd-122">**\<sectionGroup >** pour  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="1f6cd-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="1f6cd-123">Définit un espace de noms de sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="1f6cd-123">Defines a namespace for configuration sections.</span></span> |
