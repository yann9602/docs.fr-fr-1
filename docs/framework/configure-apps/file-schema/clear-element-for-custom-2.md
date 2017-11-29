---
title: "&lt;Désactivez&gt; élément de NameValueSectionHandler et DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e91c3d9693cf656a8c56c82d1997f74c2b3d64c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Désactivez >, élément pour NameValueSectionHandler et DictionarySectionHandler

Efface tous les paramètres déjà définis dans une section.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Désactivez >**

## <a name="syntax"></a>Syntaxe

```xml
<clear />
```

## <a name="attributes"></a>Attributs

Aucune

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ------------|
| [**\<sectionName >** élément](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Définit les paramètres pour les sections de configuration personnalisées qui utilisent le <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler> classes. |

## <a name="child-elements"></a>Éléments enfants

Aucune

## <a name="remarks"></a>Remarques

Vous pouvez utiliser la  **\<Effacer >** élément à supprimer de tous les paramètres de votre application qui ont été définis à un niveau supérieur dans la hiérarchie des fichiers de configuration.

## <a name="example"></a>Exemple

Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser le  **\<Effacer >** élément dans un fichier de configuration d’application pour effacer les sections définies précédemment dans le fichier de configuration machine.

Le code suivant du fichier de configuration machine déclare la section  **\<MaSection >**:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Le code suivant du fichier de configuration application supprime tous les paramètres à partir de  **\<MaSection >**. L’application ne peut pas récupérer les paramètres qui ont été déclarées dans le dans les  **\<MaSection >** section du fichier de configuration de l’ordinateur.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* les fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

[Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
