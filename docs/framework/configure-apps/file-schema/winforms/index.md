---
title: Section de configuration de Windows Forms
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b83f00f82de727812c5737915a6dc35ec98e4734
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---
# <a name="windows-forms-configuration-section"></a>Section de configuration de Windows Forms
Les paramètres de configuration de Windows Forms permettent à une application Windows Forms de stocker et d’extraire des informations sur les paramètres d’application personnalisés, par exemple la prise en charge de plusieurs écrans, la prise en charge de la haute résolution et d’autres paramètres de configuration prédéfinis.

Les paramètres de configuration de l’application Windows Forms sont stockés dans l’élément `System.Windows.Forms.ApplicationConfigurationSection` d’un fichier de configuration de l’application.

## <a name="syntax"></a>Syntaxe

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Élément  |Description |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | Ajoute une clé de paramètre de configuration avec une valeur spécifiée. |

### <a name="parent-elements"></a>Éléments parents

Élément  |Description |
---------|---------|
[\<configuration>](../configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le common language runtime et les applications Windows Forms. |

## <a name="remarks"></a>Remarques

À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework. 

L’élément `<System.Windows.Forms.ApplicationConfigurationSection>` peut contenir un ou plusieurs éléments [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) enfants, dont chacun définit un paramètre de configuration spécifique.

## <a name="see-also"></a>Voir aussi

[Schéma des fichiers de configuration](../index.md)   
[Prise en charge de la haute résolution dans Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)

