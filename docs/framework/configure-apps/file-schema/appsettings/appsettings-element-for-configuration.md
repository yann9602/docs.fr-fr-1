---
title: "&lt;appSettings&gt; , élément pour &lt;configuration&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cebb9ba7ebeb483233276324289a4ddc5a0bc381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings >, élément pour \<configuration >

Contient des paramètres d’application personnalisés. Il s’agit d’une section de configuration prédéfinie fournie par le .NET Framework.

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Attribut

|           | Description |
| --------- | ----------- |
| **fichier**  | Attribut facultatif.<br><br>Spécifie un chemin d’accès relatif vers un fichier externe qui contient les paramètres de configuration d’application personnalisés. Le fichier spécifié contient le même type de paramètres qui sont spécifiés dans le  **\<Ajouter >**,  **\<Supprimer >**, et  **\<Effacer >** éléments et utilise la même paire clé/valeur de format que ces éléments.<br><br>Le chemin d’accès spécifié est relatif au fichier de configuration principal. Pour une application Windows Forms, c’est le dossier binaire (tel que */bin/debug*), pas l’emplacement du fichier de configuration d’application. Pour les applications Web Forms, le chemin d’accès est relatif à la racine de l’application, où le *web.config* fichier se trouve.<br><br>Notez que le runtime ignore l’attribut si le fichier spécifié est introuvable. |

## <a name="parent-element"></a>Élément parent

|     | Description |
| --- | ----------- |
| [**\<configuration >** élément](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |

## <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Ajoute un paramètre d’application personnalisé. |
| [**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Efface tous les paramètres d’application définis précédemment. |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Supprime un paramètre d’application défini précédemment. |

## <a name="remarks"></a>Notes

Le  **\<appSettings >** élément stocke les informations de configuration d’application personnalisée, tels que les chaînes de connexion de base de données, les chemins d’accès de fichier, des URL de service Web XML ou d’autres informations de configuration personnalisée pour un application. Les paires clé/valeur spécifiées dans le  **\<appSettings >** élément sont accessibles dans le code à l’aide la <xref:System.Configuration.ConfigurationSettings> classe.

Vous pouvez utiliser la **fichier** d’attribut dans le  **\<appSettings >** élément de la *Web.config* et les fichiers de configuration d’application. Cet attribut spécifie un fichier de configuration qui fournit des paramètres supplémentaires ou substitue les paramètres spécifiés dans le  **\<appSettings >** élément. Le **fichier** attribut peut être utilisé dans les scénarios de développement en équipe de contrôle de code source, telles que lorsqu’un utilisateur souhaite remplacer les paramètres du projet spécifiés dans un fichier de configuration d’application.

Les fichiers de configuration spécifiés par le **fichier** attribut doit avoir un nœud racine de  **\<appSettings >** plutôt que  **\<configuration >**.

## <a name="example"></a>Exemple

L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>fichier de configuration

Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* les fichiers qui ne sont pas au niveau du répertoire d’application.

## <a name="see-also"></a>Voir aussi

[Schéma de fichier de configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
