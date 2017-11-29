---
title: "Élément personnalisé pour SingleTagSectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 496967bc3638344d2b39d428b85270b575b325ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-element-for-singletagsectionhandler"></a>Élément personnalisé pour SingleTagSectionHandler

Définit les paramètres dans une section de configuration personnalisée qui est définie par un <section> élément et utilise la <xref:System.Configuration.SingleTagSectionHandler> classe.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;*\<sectionName >*

## <a name="syntax"></a>Syntaxe

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Attributs

Attributs et valeurs d’attribut sont définies par l’utilisateur.

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

Aucune

## <a name="remarks"></a>Remarques

Le  **\<sectionName >** est un élément personnalisé défini par un [  **\<section >** ](~/docs/framework/configure-apps/file-schema/section-element.md) de balise dans le [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) élément. Le système de configuration retourne un <xref:System.Collections.IDictionary> lorsque vous appelez l’objet <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

L’exemple suivant déclare un élément personnalisé appelé  **\<sampleSection >** qui contient les paramètres lus par le <xref:System.Configuration.SingleTagSectionHandler> classe :

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
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
