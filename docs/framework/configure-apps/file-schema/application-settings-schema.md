---
title: "Schéma des paramètres d’application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
caps.latest.revision: "3"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d93a18b17e0d6b8e413903fb84dc6b427d94f6af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="application-settings-schema"></a><span data-ttu-id="c3a1f-102">Schéma des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="c3a1f-102">Application Settings schema</span></span>

<span data-ttu-id="c3a1f-103">Paramètres d’application permettent à une application Windows Forms ou ASP.NET stocker et récupérer des paramètres de portée application et de portée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="c3a1f-104">Dans ce contexte, un *paramètre* est n’importe quel élément d’information qui peut-être être spécifiques à l’application ou spécifiques à l’utilisateur actuel, quoi que ce soit à partir d’une chaîne de connexion de base de données à l’utilisateur par défaut de le taille de fenêtre par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="c3a1f-105">Par défaut, les paramètres d’application dans une application Windows Forms utilise le <xref:System.Configuration.LocalFileSettingsProvider> (classe), qui utilise le système de configuration .NET pour stocker les paramètres dans un fichier de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="c3a1f-106">Pour plus d’informations sur les fichiers utilisés par les paramètres de l’application, consultez [Architecture des paramètres d’Application](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="c3a1f-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="c3a1f-107">Paramètres de l’application définit les éléments suivants en tant que partie des fichiers de configuration qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="c3a1f-108">Élément</span><span class="sxs-lookup"><span data-stu-id="c3a1f-108">Element</span></span>                    | <span data-ttu-id="c3a1f-109">Description</span><span class="sxs-lookup"><span data-stu-id="c3a1f-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="c3a1f-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="c3a1f-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="c3a1f-111">Contient tous les  **\<paramètre >** balises spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="c3a1f-112">**\<userSettings >**</span><span class="sxs-lookup"><span data-stu-id="c3a1f-112">**\<userSettings>**</span></span>        | <span data-ttu-id="c3a1f-113">Contient tous les  **\<paramètre >** balises spécifiques à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="c3a1f-114">**\<définition >**</span><span class="sxs-lookup"><span data-stu-id="c3a1f-114">**\<setting>**</span></span>             | <span data-ttu-id="c3a1f-115">Définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-115">Defines a setting.</span></span> <span data-ttu-id="c3a1f-116">Enfant de le  **\<applicationSettings >** ou  **\<userSettings >**.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="c3a1f-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="c3a1f-117">**\<value>**</span></span>               | <span data-ttu-id="c3a1f-118">Définit une valeur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-118">Defines a setting's value.</span></span> <span data-ttu-id="c3a1f-119">Enfant de  **\<paramètre >**.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="c3a1f-120">\<applicationSettings > élément</span><span class="sxs-lookup"><span data-stu-id="c3a1f-120">\<applicationSettings> element</span></span>

<span data-ttu-id="c3a1f-121">Cet élément contient tous les  **\<paramètre >** balises qui sont spécifiques à une instance de l’application sur un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="c3a1f-122">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="c3a1f-123">\<userSettings > élément</span><span class="sxs-lookup"><span data-stu-id="c3a1f-123">\<userSettings> element</span></span>

<span data-ttu-id="c3a1f-124">Cet élément contient tous les  **\<paramètre >** balises qui sont spécifiques à l’utilisateur qui est actuellement à l’aide de l’application.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="c3a1f-125">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="c3a1f-126">\<paramètre > élément</span><span class="sxs-lookup"><span data-stu-id="c3a1f-126">\<setting> element</span></span>

<span data-ttu-id="c3a1f-127">Cet élément définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-127">This element defines a setting.</span></span> <span data-ttu-id="c3a1f-128">Il possède les attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-128">It has the following attributes.</span></span>

| <span data-ttu-id="c3a1f-129">Attribut</span><span class="sxs-lookup"><span data-stu-id="c3a1f-129">Attribute</span></span>        | <span data-ttu-id="c3a1f-130">Description</span><span class="sxs-lookup"><span data-stu-id="c3a1f-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="c3a1f-131">**name**</span><span class="sxs-lookup"><span data-stu-id="c3a1f-131">**name**</span></span>         | <span data-ttu-id="c3a1f-132">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-132">Required.</span></span> <span data-ttu-id="c3a1f-133">ID unique du paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-133">The unique ID of the setting.</span></span> <span data-ttu-id="c3a1f-134">Les paramètres créés via Visual Studio sont enregistrés avec le nom `ProjectName.Properties.Settings`.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="c3a1f-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="c3a1f-135">**serializedAs**</span></span> | <span data-ttu-id="c3a1f-136">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-136">Required.</span></span> <span data-ttu-id="c3a1f-137">Le format à utiliser pour sérialiser la valeur de texte.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="c3a1f-138">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3a1f-138">Valid values are:</span></span><br><br><span data-ttu-id="c3a1f-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-139">- `string`.</span></span> <span data-ttu-id="c3a1f-140">La valeur est sérialisée comme une chaîne à l’aide un <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="c3a1f-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-141">- `xml`.</span></span> <span data-ttu-id="c3a1f-142">La valeur est sérialisée à l’aide de la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="c3a1f-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-143">- `binary`.</span></span> <span data-ttu-id="c3a1f-144">La valeur est sérialisée en tant que binaire codé sur le texte à l’aide de la sérialisation binaire.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="c3a1f-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-145">- `custom`.</span></span> <span data-ttu-id="c3a1f-146">Le fournisseur de paramètres a une connaissance inhérente de ce paramètre et sérialise et désérialise il.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="c3a1f-147">\<valeur > élément</span><span class="sxs-lookup"><span data-stu-id="c3a1f-147">\<value> element</span></span>

<span data-ttu-id="c3a1f-148">Cet élément contient la valeur d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3a1f-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="c3a1f-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3a1f-149">Example</span></span>

<span data-ttu-id="c3a1f-150">L’exemple suivant montre un fichier de paramètres d’application qui définit deux paramètres de portée application et les deux paramètres de portée utilisateur :</span><span class="sxs-lookup"><span data-stu-id="c3a1f-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c3a1f-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3a1f-151">See also</span></span>

<span data-ttu-id="c3a1f-152">[Vue d’ensemble des paramètres d’application](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c3a1f-152">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="c3a1f-153">Architecture des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="c3a1f-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
