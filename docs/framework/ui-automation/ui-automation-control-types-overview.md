---
title: "UI Automation Control Types Overview | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI Automation, control types"
  - "control types, UI Automation"
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
caps.latest.revision: 22
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 22
---
# UI Automation Control Types Overview
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Les types de contrôle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sont des identificateurs connus qui peuvent être utilisés pour indiquer le type de contrôle que représente un élément particulier, tel qu’une zone de liste modifiable ou un bouton.  
  
 Avoir un identificateur connu permet aux périphériques de technologie d'assistance de déterminer plus facilement les types de contrôles disponibles dans l'[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] et de savoir comment interagir avec les contrôles.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## Conditions requises pour le type de contrôle UI Automation  
 Les types de contrôles [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] fournissent un jeu de conditions que les fournisseurs doivent satisfaire. Quand ces conditions sont remplies, le contrôle peut utiliser le nom du type de contrôle spécifique. Chaque type de contrôle présente des conditions pour les éléments suivants :  
  
-   Modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; quels modèles de contrôle doivent être pris en charge, lesquels sont facultatifs et lesquels ne doivent pas être pris en charge par le contrôle.  
  
-   Valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; quelles valeurs de propriété sont prises en charge.  
  
-   Arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaire pour le contrôle.  
  
 Quand un contrôle satisfait les conditions d'un type de contrôle particulier, la valeur de propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> indique ce type de contrôle.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## Types de contrôle UI Automation actuels  
 La liste suivante contient les différents types de contrôle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] actuels :  
  
-   [UI Automation Support for the Button Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [UI Automation Support for the Calendar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [UI Automation Support for the CheckBox Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [UI Automation Support for the ComboBox Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [UI Automation Support for the DataGrid Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [UI Automation Support for the DataItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [UI Automation Support for the Document Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [UI Automation Support for the Edit Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [UI Automation Support for the Group Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [UI Automation Support for the Header Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [UI Automation Support for the HeaderItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [UI Automation Support for the Hyperlink Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [UI Automation Support for the Image Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [UI Automation Support for the List Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [UI Automation Support for the ListItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [UI Automation Support for the Menu Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [UI Automation Support for the MenuBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [UI Automation Support for the MenuItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [UI Automation Support for the Pane Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [UI Automation Support for the ProgressBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [UI Automation Support for the RadioButton Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [UI Automation Support for the ScrollBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [UI Automation Support for the Separator Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [UI Automation Support for the Slider Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [UI Automation Support for the Spinner Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [UI Automation Support for the SplitButton Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [UI Automation Support for the StatusBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [UI Automation Support for the Tab Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [UI Automation Support for the TabItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [UI Automation Support for the Table Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [UI Automation Support for the Text Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [UI Automation Support for the Thumb Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [UI Automation Support for the TitleBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [UI Automation Support for the ToolBar Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [UI Automation Support for the ToolTip Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [UI Automation Support for the Tree Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [UI Automation Support for the TreeItem Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [UI Automation Support for the Window Control Type](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## Voir aussi  
 <xref:System.Windows.Automation.ControlType>