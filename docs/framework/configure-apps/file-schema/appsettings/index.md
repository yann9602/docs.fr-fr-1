---
title: "Schéma des paramètres d’application"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d51d06895e61be60bbe9153eacb2028cb32a1fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="app-settings-schema"></a><span data-ttu-id="716b7-102">Schéma des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="716b7-102">App Settings schema</span></span>

<span data-ttu-id="716b7-103">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="716b7-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="716b7-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="716b7-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="716b7-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="716b7-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="716b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="716b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="716b7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="716b7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="716b7-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="716b7-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="716b7-109">Élément</span><span class="sxs-lookup"><span data-stu-id="716b7-109">Element</span></span> | <span data-ttu-id="716b7-110">Description</span><span class="sxs-lookup"><span data-stu-id="716b7-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="716b7-111">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="716b7-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="716b7-112">Contient des balises **\<add>**, **\<clear>** et **\<remove>** pour contrôler les paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="716b7-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="716b7-113">A un attribut **file** facultatif.</span><span class="sxs-lookup"><span data-stu-id="716b7-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="716b7-114">**\<add>**</span><span class="sxs-lookup"><span data-stu-id="716b7-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="716b7-115">Définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="716b7-115">Defines a setting.</span></span> <span data-ttu-id="716b7-116">Enfant de **\<appSettings>**.</span><span class="sxs-lookup"><span data-stu-id="716b7-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="716b7-117">Requiert des attributs **key** et **value**.</span><span class="sxs-lookup"><span data-stu-id="716b7-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="716b7-118">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="716b7-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="716b7-119">Efface tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="716b7-119">Clears all settings.</span></span> <span data-ttu-id="716b7-120">Enfant de **\<appSettings>**.</span><span class="sxs-lookup"><span data-stu-id="716b7-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="716b7-121">N’a pas d’attributs.</span><span class="sxs-lookup"><span data-stu-id="716b7-121">Has no attributes.</span></span> |
| [<span data-ttu-id="716b7-122">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="716b7-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="716b7-123">Supprime un paramètre.</span><span class="sxs-lookup"><span data-stu-id="716b7-123">Removes a setting.</span></span> <span data-ttu-id="716b7-124">Enfant de **\<appSettings>**.</span><span class="sxs-lookup"><span data-stu-id="716b7-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="716b7-125">Exige un attribut **key**.</span><span class="sxs-lookup"><span data-stu-id="716b7-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="716b7-126">\<appSettings>, élément</span><span class="sxs-lookup"><span data-stu-id="716b7-126">\<appSettings> element</span></span>

<span data-ttu-id="716b7-127">Cet élément contient des balises **\<add>**, **\<clear>** et **\<remove>** pour contrôler les paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="716b7-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="716b7-128">Il définit un attribut facultatif pour **file**.</span><span class="sxs-lookup"><span data-stu-id="716b7-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="716b7-129">\<add>, élément</span><span class="sxs-lookup"><span data-stu-id="716b7-129">\<add> element</span></span>

<span data-ttu-id="716b7-130">Ajoute un paramètre d’application personnalisé en tant que paire nom/valeur à la collection de paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="716b7-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="716b7-131">Il définit les attributs pour **key** et **value**.</span><span class="sxs-lookup"><span data-stu-id="716b7-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="716b7-132">\<clear>, élément</span><span class="sxs-lookup"><span data-stu-id="716b7-132">\<clear> element</span></span>

<span data-ttu-id="716b7-133">Supprime toutes les références aux paramètres d’application personnalisés hérités et autorise uniquement les références ajoutées par les éléments **\<add>** suivant l’élément **\<clear>**.</span><span class="sxs-lookup"><span data-stu-id="716b7-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="716b7-134">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="716b7-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="716b7-135">\<remove>, élément</span><span class="sxs-lookup"><span data-stu-id="716b7-135">\<remove> element</span></span>

<span data-ttu-id="716b7-136">Supprime une référence à un paramètre d’application personnalisé hérité de la collection de paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="716b7-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="716b7-137">Il définit un attribut pour **key**.</span><span class="sxs-lookup"><span data-stu-id="716b7-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="716b7-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="716b7-138">Example</span></span>

<span data-ttu-id="716b7-139">L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :</span><span class="sxs-lookup"><span data-stu-id="716b7-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="716b7-140">L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :</span><span class="sxs-lookup"><span data-stu-id="716b7-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="716b7-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="716b7-141">See also</span></span>

<span data-ttu-id="716b7-142">[Vue d’ensemble des paramètres d’application](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="716b7-142">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="716b7-143">Architecture des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="716b7-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
