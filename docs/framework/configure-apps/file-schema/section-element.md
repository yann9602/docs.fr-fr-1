---
title: "&lt;section&gt; élément"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8ed8b0211c8366d799fe158d91dcb42f92ad0cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="section-element"></a>\<section > élément

Contient une déclaration de section de configuration.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<section >**

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section >**

## <a name="syntax"></a>Syntaxe

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Attributs requis

|           | Description |
| --------- | ----------- |
| **name**  | Spécifie le nom de la section de configuration. |
| **type**  | Spécifie le nom de la classe de gestionnaire de section de configuration qui lit la section du fichier de configuration. La valeur de type a la syntaxe « fully-qualified-section-handler-class-name, nom d’assembly simple ». Le nom simple d’assembly est le nom de fichier racine sans le *.dll* extension de fichier. |

## <a name="optional-attributes"></a>Attributs facultatifs

Les attributs suivants sont appliquent uniquement aux applications ASP.NET. Le système de configuration ignore ces attributs pour les autres types d’applications.

|                     | Description |
| ------------------- | ----------- |
| **allowDefinition** | Spécifie la section peut être utilisée dans le fichier de configuration. Utilisez l'une des valeurs suivantes :<br><br>**Partout**<br>Permet à la section peut être utilisée dans n’importe quel fichier de configuration. Il s'agit de la valeur par défaut.<br>**MachineOnly**<br>Autorise la section à être utilisé uniquement dans le fichier de configuration machine (*Machine.config*).<br>**MachineToApplication**<br>Autorise la section à utiliser dans le fichier de configuration machine ou dans le fichier de configuration d’application. |
| **allowLocation**   | Détermine si la section peut être utilisée dans le  **\<emplacement >** élément. Utilisez l'une des valeurs suivantes :<br><br>**true**<br>La section au sein de la  **\<emplacement >** élément. Il s'agit de la valeur par défaut.<br>**false**<br>N’autorise pas la section au sein de la  **\<emplacement >** élément. |

## <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [**\<configSections >** élément](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Contient des déclarations d’espace de noms et de la section de configuration. |
| [**\<sectionGroup >** élément](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Définit un espace de noms de sections de configuration. |

> [!NOTE]
> A  **\<section >** élément est un élément enfant d’un  **\<configSections >** ou  **\<sectionGroup >** mais pas les deux.

## <a name="child-elements"></a>Éléments enfants

Aucune

## <a name="remarks"></a>Remarques

Déclaration essentiellement d’une section de configuration définit un nouvel élément pour le fichier de configuration. Le nouvel élément contient une configuration de gestionnaire de section de paramètres (autrement dit, une classe qui implémente le <xref:System.Configuration.IConfigurationSectionHandler> interface) lit. Les attributs et les éléments enfants d’une section que vous définissez dépendent du Gestionnaire de section que vous permet de lire vos paramètres.

Déclaration d’un gestionnaire de section de configuration dans le *Machine.config* fichier vous permet d’utiliser la section de configuration dans n’importe quel fichier de configuration d’application sur cet ordinateur, à moins que le **allowDefinition**attribut spécifie dans le cas contraire.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une section de configuration et de définir les paramètres de cette section :

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* les fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

[Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
