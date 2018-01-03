---
title: "&lt;linkedConfiguration&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dffff7fefa80f420e61045b21b0e0c1a170e2911
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > élément

Spécifie un fichier de configuration à inclure.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration >**

## <a name="syntax"></a>Syntaxe

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **href**  | Attribut requis.<br><br>L’URL du fichier de configuration à inclure. Le seul format pris en charge pour le **href** attribut est `file://`. Fichiers locaux et les fichiers UNC sont pris en charge. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [**\<assemblyBinding >** élément](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Spécifie la stratégie de liaison de l’assembly au niveau de la configuration. |

## <a name="child-elements"></a>Éléments enfants

Aucun.

## <a name="remarks"></a>Notes

Le  **\<linkedConfiguration >** élément simplifie la maintenance pour les assemblys de composant. Si une ou plusieurs applications utilisent un assembly disposant d’un fichier de configuration qui réside dans un emplacement connu, les fichiers de configuration des applications qui utilisent l’assembly peuvent utiliser le  **\<linkedConfiguration >** élément à inclure le fichier de configuration d’assembly, au lieu d’y compris les informations de configuration directement. Lorsque l’assembly de composant est prise en charge, la mise à jour le fichier de configuration commun fournit des informations de configuration mise à jour pour toutes les applications qui utilisent l’assembly.

> [!NOTE]
> Le  **\<linkedConfiguration >** élément n’est pas pris en charge pour les applications avec des manifestes côte à côte de Windows.

Les règles suivantes régissent l’utilisation des fichiers de configuration liés :

- Les paramètres dans les fichiers de configuration inclus uniquement affectent la stratégie de liaison du chargeur et sont utilisés uniquement par le chargeur. Les fichiers de configuration inclus peuvent avoir des paramètres autres que les stratégies de liaison, mais ces paramètres n’ont aucun effet.

- Le seul format pris en charge pour le `href` attribut est `file://`. Fichiers locaux et les fichiers UNC sont pris en charge.

- Il n’existe aucune contrainte sur le nombre de configurations liées par fichier de configuration.

- Tous les fichiers de configuration liés sont fusionnés pour former un fichier, semblable au comportement de la `#include` directive en C/C++.

- Le  **\<linkedConfiguration >** élément est autorisé uniquement dans les fichiers de configuration d’application ; il est ignoré dans *Machine.config*.

- Les références circulaires sont détectées et arrêtées. Autrement dit, si le  **\<linkedConfiguration >** les éléments d’une série de fichiers de configuration forment une boucle, la boucle est détectée et arrêtée.

## <a name="example"></a>Exemple

L’exemple suivant montre comment inclure le fichier de configuration à partir du disque dur local :

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Voir aussi

[**\<assemblyBinding >** élément](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
[Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
