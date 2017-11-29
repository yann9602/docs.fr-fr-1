---
title: "&lt;ajouter&gt; , élément pour &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b00af6f7d735d5db8fd746205ba225253cad133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="9ee8b-102">\<Ajouter >, élément pour \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="9ee8b-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="9ee8b-103">Ajoute un paramètre d’application personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9ee8b-103">Adds a custom application setting.</span></span>

<span data-ttu-id="9ee8b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9ee8b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9ee8b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="9ee8b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="9ee8b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="9ee8b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9ee8b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ee8b-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="9ee8b-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="9ee8b-108">Attributes</span></span>

|           | <span data-ttu-id="9ee8b-109">Description</span><span class="sxs-lookup"><span data-stu-id="9ee8b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="9ee8b-110">**key**</span><span class="sxs-lookup"><span data-stu-id="9ee8b-110">**key**</span></span>   | <span data-ttu-id="9ee8b-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9ee8b-111">Required attribute.</span></span><br><br><span data-ttu-id="9ee8b-112">Spécifie le nom de la clé à ajouter.</span><span class="sxs-lookup"><span data-stu-id="9ee8b-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="9ee8b-113">**value**</span><span class="sxs-lookup"><span data-stu-id="9ee8b-113">**value**</span></span> | <span data-ttu-id="9ee8b-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9ee8b-114">Required attribute.</span></span><br><br><span data-ttu-id="9ee8b-115">Spécifie la valeur de la clé à ajouter.</span><span class="sxs-lookup"><span data-stu-id="9ee8b-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="9ee8b-116">Élément parent</span><span class="sxs-lookup"><span data-stu-id="9ee8b-116">Parent element</span></span>

|     | <span data-ttu-id="9ee8b-117">Description</span><span class="sxs-lookup"><span data-stu-id="9ee8b-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9ee8b-118">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="9ee8b-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="9ee8b-119">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="9ee8b-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9ee8b-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9ee8b-120">Child elements</span></span>

<span data-ttu-id="9ee8b-121">Aucune</span><span class="sxs-lookup"><span data-stu-id="9ee8b-121">None</span></span>

## <a name="example"></a><span data-ttu-id="9ee8b-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ee8b-122">Example</span></span>

<span data-ttu-id="9ee8b-123">L’exemple suivant montre comment ajouter un paramètre de configuration personnalisée pour le nom de l’application :</span><span class="sxs-lookup"><span data-stu-id="9ee8b-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="9ee8b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ee8b-124">See also</span></span>

[<span data-ttu-id="9ee8b-125">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ee8b-125">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
