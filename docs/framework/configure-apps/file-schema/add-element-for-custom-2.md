---
title: "&lt;ajouter&gt; élément de NameValueSectionHandler et DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e9dc671f0df9034410d20fdf69862884d6b3b300
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Ajouter >, élément pour NameValueSectionHandler et DictionarySectionHandler

Ajoute des paramètres d’application personnalisés. Chaque  **\<Ajouter >** balise contient une paire clé/valeur.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Ajouter >**

## <a name="syntax"></a>Syntaxe

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Attributs

| Attribut | Description |
| --------- | ----------- |
| **key**   | Attribut requis.<br><br>Spécifie le nom du paramètre. |
| **value** | Attribut requis.<br><br>Spécifie la valeur du paramètre. |

## <a name="parent-element"></a>Élément parent

| Élément | Description |
| ------- | ------------|
| [**\<sectionName >** élément](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Définit les paramètres pour les sections de configuration personnalisées qui utilisent le <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> classes. |

## <a name="child-elements"></a>Éléments enfants

Aucune

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir une section de configuration personnalisée et utiliser le  **\<Ajouter >** élément de placer les paramètres dans la section :

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* les fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

[Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
