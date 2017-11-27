---
title: "&lt;supprimer&gt; , élément pour &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 10202a38d54e4c9744dbd20fb5f226fa41f5dab5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="09e21-102">\<Supprimer >, élément pour \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="09e21-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="09e21-103">Supprime les paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="09e21-103">Removes custom application settings.</span></span>

<span data-ttu-id="09e21-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="09e21-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="09e21-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="09e21-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="09e21-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Supprimer >**</span><span class="sxs-lookup"><span data-stu-id="09e21-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="09e21-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09e21-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="09e21-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="09e21-108">Attribute</span></span>

|         | <span data-ttu-id="09e21-109">Description</span><span class="sxs-lookup"><span data-stu-id="09e21-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="09e21-110">**key**</span><span class="sxs-lookup"><span data-stu-id="09e21-110">**key**</span></span> | <span data-ttu-id="09e21-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="09e21-111">Required attribute.</span></span><br><br><span data-ttu-id="09e21-112">Spécifie le nom de la clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="09e21-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="09e21-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="09e21-113">Parent element</span></span>

|     | <span data-ttu-id="09e21-114">Description</span><span class="sxs-lookup"><span data-stu-id="09e21-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="09e21-115">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="09e21-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="09e21-116">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="09e21-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="09e21-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="09e21-117">Child elements</span></span>

<span data-ttu-id="09e21-118">Aucune</span><span class="sxs-lookup"><span data-stu-id="09e21-118">None</span></span>

## <a name="example"></a><span data-ttu-id="09e21-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="09e21-119">Example</span></span>

<span data-ttu-id="09e21-120">L’exemple suivant montre comment supprimer un paramètre de configuration personnalisée pour `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="09e21-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="09e21-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09e21-121">See also</span></span>

[<span data-ttu-id="09e21-122">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="09e21-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
