---
title: "&#201;v&#233;nements UI Automation pour les clients | Microsoft Docs"
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
  - "UI Automation, les événements pour les clients"
  - "événements, les clients UI Automation"
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
caps.latest.revision: 32
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 32
---
# &#201;v&#233;nements UI Automation pour les clients
> [!NOTE]
>  Cette documentation est destinée aux développeurs .NET Framework qui veulent utiliser managé [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes définies dans le <xref:System.Windows.Automation> espace de noms. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique décrit comment [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] événements sont utilisés par les clients UI Automation.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]permet aux clients de s’abonner aux événements d’intérêt. Cette fonctionnalité améliore les performances en éliminant le besoin d’interroger continuellement tous les [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] des éléments dans le système pour voir si des informations, la structure ou l’état a changé.  
  
 L’efficacité est également améliorée par la possibilité d’écouter des événements uniquement dans une portée définie. Par exemple, un client peut écouter des événements de modification de focus sur tous les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] les éléments dans l’arborescence ou sur un seul élément et ses descendants.  
  
> [!NOTE]
>  Ne supposez pas que tous les événements possibles sont déclenchés par un [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] fournisseur. Par exemple, toutes les modifications de propriété entraînent des événements soient déclenchés par les fournisseurs de proxys standard pour [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] des contrôles.  
  
 Pour une vue plus large de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] les événements, consultez [vue d’ensemble des événements UI Automation](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Abonnement à des événements  
 Les applications clientes s’abonnent à des événements d’un type particulier en inscrivant un gestionnaire d’événements, à l’aide de l’une des méthodes suivantes.  
  
|Méthode|Type d'événement|Type d'arguments d'événement|Type délégué|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Modification du focus|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Modification de propriété|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Modification de la structure|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Tous les autres événements, identifiés par un <xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> ou <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Avant d’appeler la méthode, vous devez créer une méthode déléguée pour gérer l’événement. Si vous préférez, vous pouvez gérer différents types d’événements dans une seule méthode et passer cette méthode dans plusieurs appels à l’une des méthodes du tableau. Par exemple, un seul <xref:System.Windows.Automation.AutomationEventHandler> peut être configuré pour gérer divers événements différemment en fonction de la <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
>  Pour traiter les événements de fermeture de fenêtre, convertir le type d’argument passé au gestionnaire d’événements en tant que <xref:System.Windows.Automation.WindowClosedEventArgs>. Étant donné que la [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] élément de la fenêtre n’est plus valide, vous ne pouvez pas utiliser le `sender` paramètre pour récupérer des informations ; utiliser <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> à la place.  
  
> [!CAUTION]
>  Si votre application peut recevoir des événements de sa propre [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], n’utilisez pas de votre application [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread s’abonner aux événements ou pour annuler l’abonnement. Cela peut entraîner un comportement imprévisible. Pour plus d’informations, consultez [problèmes de threads UI Automation](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Lors de l’arrêt, ou lorsque [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] événements ne sont plus intéressants à l’application, les clients UI Automation doivent appeler l’une des méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Annule l’inscription d’un gestionnaire d’événements qui a été enregistré à l’aide de <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Annule l’inscription d’un gestionnaire d’événements qui a été enregistré à l’aide de <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Annule l’inscription d’un gestionnaire d’événements qui a été enregistré à l’aide de <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Annule l’inscription de tous les gestionnaires d’événements inscrits.|  
  
 Par exemple de code, consultez [s’abonner à des événements UI Automation](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Voir aussi  
 [S’abonner à des événements UI Automation](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)   
 [Vue d’ensemble des événements UI Automation](../../../docs/framework/ui-automation/ui-automation-events-overview.md)   
 [Vue d’ensemble des propriétés UI Automation](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)   
 [Exemple de TrackFocus](http://msdn.microsoft.com/fr-fr/4a91c0af-6bb5-4d38-a743-cf136f268fc9)