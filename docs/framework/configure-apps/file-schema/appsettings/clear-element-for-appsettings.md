---
title: "&lt;Désactivez&gt; , élément pour &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ac1e9a86d0c3e1bb1f23b753fd9867effef03ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="1a103-102">\<Désactivez >, élément pour \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="1a103-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="1a103-103">Efface les paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="1a103-103">Clears custom application settings.</span></span>

<span data-ttu-id="1a103-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1a103-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="1a103-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="1a103-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="1a103-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Désactivez >**</span><span class="sxs-lookup"><span data-stu-id="1a103-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1a103-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a103-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="1a103-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="1a103-108">Attributes</span></span>

<span data-ttu-id="1a103-109">Aucune</span><span class="sxs-lookup"><span data-stu-id="1a103-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="1a103-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="1a103-110">Parent element</span></span>

|     | <span data-ttu-id="1a103-111">Description</span><span class="sxs-lookup"><span data-stu-id="1a103-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1a103-112">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="1a103-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="1a103-113">Contient des paramètres d’application personnalisés, tels que les chemins d’accès, des URL de service Web XML ou toute autre information de configuration d’application personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1a103-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="1a103-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1a103-114">Child elements</span></span>

<span data-ttu-id="1a103-115">Aucune</span><span class="sxs-lookup"><span data-stu-id="1a103-115">None</span></span>

## <a name="example"></a><span data-ttu-id="1a103-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a103-116">Example</span></span>

<span data-ttu-id="1a103-117">L’exemple suivant montre comment effacer les paramètres de configuration personnalisée :</span><span class="sxs-lookup"><span data-stu-id="1a103-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="1a103-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a103-118">See also</span></span>

[<span data-ttu-id="1a103-119">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1a103-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
