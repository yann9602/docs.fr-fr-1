---
title: "Vue d'ensemble des types de contrôle UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c1a424f05f2d57f773e8367e102f553d69b7dc22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-control-types-overview"></a>Vue d'ensemble des types de contrôle UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Les types de contrôle[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sont des identificateurs connus qui peuvent être utilisés pour indiquer le type de contrôle que représente un élément particulier, tel qu’une zone de liste modifiable ou un bouton.  
  
 Avoir un identificateur connu permet aux périphériques de technologie d'assistance de déterminer plus facilement les types de contrôles disponibles dans l' [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] et de savoir comment interagir avec les contrôles.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>Conditions requises pour le type de contrôle UI Automation  
 Les types de contrôles[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] fournissent un jeu de conditions que les fournisseurs doivent satisfaire. Quand ces conditions sont remplies, le contrôle peut utiliser le nom du type de contrôle spécifique. Chaque type de contrôle présente des conditions pour les éléments suivants :  
  
-   Modèles de contrôle[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; quels modèles de contrôle doivent être pris en charge, lesquels sont facultatifs et lesquels ne doivent pas être pris en charge par le contrôle.  
  
-   Valeurs de propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; quelles valeurs de propriété sont prises en charge.  
  
-   Arborescence[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaire pour le contrôle.  
  
 Quand un contrôle satisfait les conditions d'un type de contrôle particulier, la valeur de propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> indique ce type de contrôle.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Types de contrôle UI Automation actuels  
 La liste suivante contient les différents types de contrôle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] actuels :  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Button](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Calendar](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle de case à cocher](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle ComboBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle DataGrid](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle DataItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Document](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Edit](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Group](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Header](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle HeaderItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Hyperlink](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Image](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle List](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle ListItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Menu](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle MenuBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle MenuItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Pane](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle ProgressBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle RadioButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle de barre de défilement](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Separator](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Slider](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Spinner](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle SplitButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle StatusBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Tab](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle TabItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Table](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Text](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Thumb](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle TitleBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle de barre d’outils](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle d’info-bulle](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Tree](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [Prise en charge d’UI Automation pour le Type de contrôle Window](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Automation.ControlType>
