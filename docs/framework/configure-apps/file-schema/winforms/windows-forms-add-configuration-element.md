---
title: "Windows Forms ajoutent l’élément de Configuration"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 828a28769e164535d4dde989ef8cce91caf9cb48
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2017
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms ajoutent l’élément de Configuration

Le `<add>` élément ajoute une clé prédéfinie qui spécifie si votre application Windows Form prend en charge les fonctionnalités ajoutées aux applications Windows Forms dans les 4.7 Framework .NET ou version ultérieure.

## <a name="syntax"></a>Syntaxe

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

| Attribut | Description |
| --------- | ----------- |
| `key`     | Attribut requis. Nom de clé prédéfini qui correspond à une fonctionnalité personnalisable particulière de Windows Forms. |
| `value`   | Attribut requis. La valeur à affecter au `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key`noms d’attributs et valeurs associées

| Nom `key` | Valeurs | Description |
| ---------- | ------ | ----------- |
| « AnchorLayout.DisableSinglePassControlScaling » | « true » &#124; » False » | Indique si les contrôles ancrés sont mis à l’échelle en un seul passage. passer des « true » pour désactiver la seule mise à l’échelle ; Sinon, false. Consultez la section « Unique pass mise à l’échelle » dans le [remarques](#Remarks) pour plus d’informations. |
| « DpiAwareness » | « PerMonitorV2 » &#124; » False » | Indique si une application prend en charge DPI. Définir la clé « PerMonitorV2 » pour prendre en charge une reconnaissance de résolution ; Sinon, affectez-lui la valeur « false ». Reconnaissance de résolution est une fonctionnalité d’abonnement ; Pour tirer parti de la prise en charge DPI élevée de Windows Forms, vous devez définir sa valeur sur « PerMonitorV2 ». Consultez le [notes](#remarks) section pour plus d’informations. |
| « CheckedListBox.DisableHighDpiImprovements » | « true » &#124; » False » | Indique si le <xref:System.Windows.Forms.CheckedListBox> contrôle tire parti de la mise à l’échelle et la disposition des améliorations introduites dans le 4.7 Framework .NET. « true » pour ne pas les améliorations de mise en page et caling ; Sinon, « false ». |
| « DataGridView.DisableHighDpiImprovements » | « true » &#124; » False » | Indique si le <xref:System.Windows.Forms.DataGridView> contrôler la mise à l’échelle et la disposition des améliorations introduites dans le 4.7 Framework .NET. « true » pour quitter la reconnaissance de résolution ; « false » dans le cas contraire. |
| « DisableDpiChangedMessageHandling » | « true » &#124; » False » | « true » pour refuser de recevoir des messages relatifs à l’échelle des modifications ; résolution « false » dans le cas contraire. Consultez le [notes](#remarks) section pour plus d’informations. |
| « EnableWindowsFormsHighDpiAutoResizing » | « true » &#124; » False » | Indique si une application Windows Forms est automatiquement redimensionnée en raison de modifications de mise à l’échelle PPP. « true » pour activer le redimensionnement automatique ; Sinon, false. |
| « Form.DisableSinglePassControlScaling » | « true » &#124; » False » | Indique si le <xref:System.Windows.Forms.Form> est mis à l’échelle en un seul passage. simple-pass « true » pour désactiver la mise à l’échelle ; Sinon, false. Consultez la section « Unique pass mise à l’échelle » dans le [remarques](#Remarks) pour plus d’informations. |
| « MonthCalendar.DisableSinglePassControlScaling » | « true » &#124; » False » | Indique si le <xref:System.Windows.Forms.MonthCalendar> contrôle est mis à l’échelle en un seul passage. simple-pass « true » pour désactiver la mise à l’échelle ; Sinon, false. Consultez la section « Unique pass mise à l’échelle » dans le [remarques](#Remarks) pour plus d’informations. |
| « Toolstrip.DisableHighDpiImprovements » | « true » &#124; » False » | Indique si le <xref:System.Windows.Forms.ToolStrip> contrôle tire parti de la mise à l’échelle et la disposition des améliorations introduites dans le 4.7 Framework .NET. « true » pour quitter la reconnaissance de résolution ; « false » dans le cas contraire. |

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Configure la prise en charge des nouvelles fonctionnalités d’application Windows Forms. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" />Section Notes

À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework. 

Le `<System.Windows.Forms.ApplicationConfigurationSection>` élément vous permet d’ajouter un ou plusieurs enfants `<add>` éléments, chacune définissant un paramètre de configuration spécifique.  

Pour une vue d’ensemble de la prise en charge de Windows Forms haute résolution, consultez [prennent en charge DPI de haute dans les Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Les applications Windows Forms qui s’exécutent sous les versions de Windows depuis Windows 10 Édition créateurs et cibler des versions du .NET Framework en commençant par le 4.7 Framework .NET peuvent être configurées pour tirer parti des améliorations de PPP élevées introduites dans le .NET Framework 4.7. Elles incluent notamment :

- Prise en charge des scénarios de résolution dynamiques dans lequel l’utilisateur modifie le facteur PPP ou à l’échelle une fois une application Windows Forms a été lancée.

- Améliorations apportées à la mise à l’échelle et la disposition d’un nombre de Windows Forms contrôles, tels que les <xref:System.Windows.Forms.MonthCalendar> contrôle et la <xref:System.Windows.Forms.CheckedListBox> contrôle. 

Reconnaissance de haute résolution est une fonctionnalité d’abonnement ; par défaut, la valeur de `DpiAwareness` est `false`. Vous pouvez choisir dans la prise en charge des Windows Forms pour la reconnaissance de résolution en définissant la valeur de cette clé à `PerMonitorV2` dans le fichier de configuration d’application. Si une reconnaissance de résolution est activée, toutes les fonctionnalités PPP individuelles sont également activées. Elles incluent notamment :

- PPP modifié des messages, qui sont contrôlés par le `DisableDpiChangedMessageHandling` clé.

- PPP prise en charge dynamique, qui est contrôlée par le `EnableWindowsFormsHighDpiAutoResizing` clé.

- Seul passage mise à l’échelle du contrôle, qui est contrôlé par le `Form.DisableSinglePassControlScaling` de chaque <xref:System.Windows.Forms.Form> des contrôles, en le `AnchorLayout.DisableSinglePassControlScaling` clés pour les contrôles ancrés et par le `MonthCalendar.DisableSinglePassControlScaling` clé pour la <xref:System.Windows.Forms.MonthCalendar> contrôle 

- Haute résolution mise à l’échelle et la disposition améliorations, qui est contrôlé par le `CheckListBox.DisableHighDpiImprovements` clé pour la <xref:System.Windows.Forms.CheckedListBox> contrôler, par le `DataGridView.DisableHighDpiImprovements` clé pour la <xref:System.Windows.Forms.DataGridView> (contrôle) et par le `Toolstrip.DisableHighDpiImprovements` clé pour la <xref:System.Windows.Forms.ToolStrip> contrôle.  

Le paramètre de participer unique par défaut fourni par le paramètre `DpiAwareness` à `PerMonitorV2` est généralement suffisant pour les nouvelles applications Windows Forms. Toutefois, vous pouvez ensuite désactiver des améliorations PPP élevées en ajoutant la clé correspondante dans le fichier de configuration d’application. Par exemple, pour tirer parti de toutes les featuers PPP nouvelle à l’exception de prise en charge de PPP dynamique, vous devez ajouter les éléments suivants à votre fichier de configuration d’application :

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <--! Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
En règle générale, vous refuser une fonctionnalité particulière, car vous avez choisi de gérer par programmation.

Pour plus d’informations sur comment tirer profit de prise en charge des résolutions élevées dans les applications Windows Forms, consultez [prennent en charge DPI de haute dans les Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

À compter de la 4.7 Framework .NET, les contrôles Windows Forms déclenchent un nombre d’événements liés aux modifications de la mise à l’échelle PPP. Celles-ci incluent la <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, et <xref:System.Windows.Forms.Form.DpiChanged> événements. La valeur de la `DisableDpiChangedMessageHandling` clé détermine si ces événements sont déclenchés dans une application Windows Forms. 

### <a name="single-pass-scaling"></a>Seul passage mise à l’échelle

La mise à l’échelle unique ou passer plusieurs d’influence sur la réactivité perçue de l’interface utilisateur et l’apparence visuelle des éléments d’interface utilisateur comme ils sont mis à l’échelle. À compter de la 4.7 Framework .NET, Windows Forms utilise mise à l’échelle d’une seule passe. Dans les versions précédentes du .NET Framework, la mise à l’échelle a été effectuée via plusieurs passes, ce qui a provoqué des contrôles à l’échelle plus de données nécessaires. Mise à l’échelle de passage unique doit être désactivée uniquement si votre application dépend de l’ancien comportement.  

## <a name="see-also"></a>Voir aussi
 
[Section de Configuration de Windows Forms](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Prise en charge de la haute résolution dans Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
