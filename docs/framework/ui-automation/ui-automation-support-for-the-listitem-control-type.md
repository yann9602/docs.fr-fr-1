---
title: "Prise en charge d'UI Automation pour le type de contrôle ListItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d6705aea3958697c466deb5ca1f9dc45b9f27f31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Prise en charge d'UI Automation pour le type de contrôle ListItem
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique fournit des informations sur la prise en charge d’ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle <xref:System.Windows.Automation.ControlType.ListItem> . Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit réunir pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Les conditions incluent des indications spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Les contrôles d’élément de liste constituent un exemple de contrôles qui implémentent le type de contrôle ListItem.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nécessaires pour le type de contrôle ListItem. Les spécifications [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles de liste, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Arborescence UI Automation obligatoire  
 Le tableau suivant représente l’affichage de contrôle et l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles d’élément de liste. En outre, il décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , consultez [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|------------------|------------------|  
|ListItem<br /><br /> -Image (0 ou plus)<br />-Texte (0 ou plus)<br />-Edit (0 ou plus)|ListItem|  
  
 Les enfants d’un contrôle d’élément de liste dans l’affichage du contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] doivent toujours correspondre à la valeur « 0 ». Si la structure du contrôle est telle que les autres éléments sont contenus sous l’élément de liste, elle doit suivre les conditions requises pour le [prise en charge d’UI Automation pour le Type de contrôle TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md) type de contrôle.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles d’élément de liste. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriétés, consultez [propriétés UI Automation pour les Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propriété[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] |Value|Notes|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les notes.|La valeur de cette propriété doit être unique dans tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les notes.|La valeur de cette propriété doit inclure la zone de contenu de l’image et du texte de l’élément de liste.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Selon le cas|Si le contrôle de liste a un point interactif (point sur lequel l’utilisateur clique pour que la liste prenne le focus), ce point doit être exposé via cette propriété. Si le contrôle de liste est intégralement couvert par les éléments de liste descendants, il déclenche <xref:System.Windows.Automation.NoClickablePointException> pour indiquer que le client doit demander un point interactif à un élément du contrôle de liste.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les notes.|La valeur de propriété du nom d’un contrôle d’élément de liste provient du contenu textuel de l’élément.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consultez les notes.|S’il existe une étiquette de texte statique, cette propriété doit exposer une référence à ce contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ListItem|Cette valeur est identique pour toutes les infrastructures d’interface utilisateur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"élément de liste"|Chaîne localisée correspondant au type de contrôle ListItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Le contrôle de liste est toujours inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle de liste est toujours inclus dans l’affichage de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Si le conteneur peut accepter l’entrée au clavier, cette propriété doit avoir la valeur true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Le texte d’aide des contrôles de liste doit expliquer pourquoi l’utilisateur est amené à faire un choix dans une liste d’options. Il s’agit généralement du même type d’informations que dans une info-bulle. Par exemple, « Sélectionnez un élément pour définir la résolution de votre moniteur ».|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Selon le cas|Cette propriété doit être exposée pour les contrôles d’élément de liste qui représentent un objet sous-jacent. Ces contrôles d’élément de liste ont généralement une icône associée au contrôle que les utilisateurs associent à l’objet sous-jacent.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Selon le cas|Cette propriété doit retourner une valeur indiquant si l’élément de liste fait actuellement l’objet d’un défilement dans le conteneur parent qui implémente le modèle de contrôle Scroll.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Modèles de contrôle UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par les contrôles d’élément de liste. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Assistance|Notes|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Oui|Le contrôle d’élément de liste doit implémenter ce modèle de contrôle. Cela permet aux contrôles d’élément de liste de transmettre des informations quand ils sont sélectionnés.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Selon le cas|Si l’élément de liste est contenu dans un conteneur pouvant faire l’objet d’un défilement, ce modèle de contrôle doit être implémenté.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Selon le cas|Si l’élément de liste est sélectionnable et si l’action n’effectue pas de changement d’état de sélection, ce modèle de contrôle doit être implémenté.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Selon le cas|Si l’élément peut être manipulé pour afficher ou masquer des informations, ce modèle de contrôle doit être implémenté.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Selon le cas|Si l’élément peut être modifié, ce modèle de contrôle doit être implémenté. Les changements apportés au contrôle d’élément de liste entraînent des modifications des valeurs de <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>et <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Selon le cas|Si la navigation spatiale d’un élément à un autre est prise en charge dans le conteneur de liste, et si le conteneur est organisé en lignes et en colonnes, le modèle de contrôle GridItem doit être implémenté.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Selon le cas|Si l’élément comporte une commande (distincte de la sélection) qui peut être effectuée sur celui-ci, ce modèle doit être implémenté. Il s’agit généralement d’une action associée au double-clic sur le contrôle d’élément de liste. C’est le cas, par exemple, du lancement d’un document à partir de l’ [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], ou de la lecture d’un fichier de musique dans [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)].|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Événements UI Automation obligatoires  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles d’élément de liste. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Événement[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] |Assistance|Notes|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Selon le cas|Aucun.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Obligatoire|Aucun.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Obligatoire|Aucun.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Obligatoire|Aucun.|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> |Obligatoire|Aucun.|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatoire|Aucun.|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatoire|Aucun.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Obligatoire|Aucun.|  
|Événement de modification de propriété<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty> .|Selon le cas|Aucun.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> |Selon le cas|Aucun.|  
|Événement de modification de propriété<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> |Selon le cas|Aucun.|  
|Événement de modification de propriété<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> |Selon le cas|Aucun.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Automation.ControlType.ListItem>  
 [Vue d’ensemble des types de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Vue d’ensemble d’UI Automation](../../../docs/framework/ui-automation/ui-automation-overview.md)
