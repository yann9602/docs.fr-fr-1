---
title: "UI Automation Support for the HeaderItem Control Type | Microsoft Docs"
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
  - "UI Automation, Header Item control type"
  - "Header Item control type"
  - "control types, Header Item"
ms.assetid: 09ce1310-ee31-493c-a71e-010bafc42fcf
caps.latest.revision: 20
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 20
---
# UI Automation Support for the HeaderItem Control Type
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique fournit des informations sur la prise en charge d’[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle HeaderItem. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est l’ensemble de conditions qu’un contrôle doit réunir pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. Les conditions incluent des recommandations spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], les valeurs des propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Le type de contrôle HeaderItem fournit une étiquette visuelle pour une ligne ou une colonne d’informations.  
  
 Les contrôles header item sont des exemples de contrôles qui implémentent le type de contrôle HeaderItem. Les spécifications [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] décrites dans les sections suivantes s’appliquent à tous les contrôles header, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## Arborescence UI Automation requise  
 Le tableau suivant représente l’affichage de contrôle et l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] concernant les contrôles header item et décrit ce que peut contenir chaque affichage. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Affichage de contrôle|Affichage de contenu|  
|---------------------------|--------------------------|  
|HeaderItem|None|  
  
<a name="Required_UI_Automation_Properties"></a>   
## Propriétés UI Automation obligatoires  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement adaptée aux contrôles header item. Pour plus d’informations sur les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Notes|  
|-------------------------------------------------------------------------------------|------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les remarques.|La valeur de cette propriété doit être unique dans tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les remarques.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consultez les remarques.|Pris en charge s’il existe un rectangle englobant. Si les points du rectangle englobant ne sont pas tous interactifs et que vous effectuez un test de positionnement spécialisé, vous devez substituer et fournir une zone interactive.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les remarques.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les remarques.|Le contrôle header item est toujours à étiquetage automatique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`.|Les contrôles header item n’ont pas d’étiquette statique.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|HeaderItem|Cette valeur est la même pour toutes les infrastructures d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« élément d’en\-tête »|Chaîne localisée pour le type de contrôle HeaderItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Le contrôle header item n’est pas inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Le contrôle header item est toujours inclus dans l’affichage de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Consultez les remarques.|Cette propriété fournit des informations pour les ordres de tri par élément d’en\-tête.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## Modèles de contrôle UI Automation obligatoires  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles header item. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Prise en charge|Notes|  
|------------------------|---------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Selon le cas|Implémentez ce modèle de contrôle si le contrôle header item peut être redimensionné.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Selon le cas|Implémentez ce modèle de contrôle si un clic sur le contrôle header item permet de trier les données.|  
  
<a name="Required_UI_Automation_Events"></a>   
## Événements UI Automation obligatoires  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles header item. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Événement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge|Notes|  
|-------------------------------------------------------------------------------------|---------------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Selon le cas|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Obligatoire|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|Aucun|  
  
## Voir aussi  
 <xref:System.Windows.Automation.ControlType.HeaderItem>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)