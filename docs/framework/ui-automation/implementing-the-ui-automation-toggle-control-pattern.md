---
title: "Implementing the UI Automation Toggle Control Pattern | Microsoft Docs"
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
  - "Toggle control pattern"
  - "control patterns, Toggle"
  - "UI Automation, Toggle control pattern"
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
caps.latest.revision: 19
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 19
---
# Implementing the UI Automation Toggle Control Pattern
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IToggleProvider>, notamment des informations sur les méthodes et les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.TogglePattern> est utilisé pour prendre en charge les contrôles qui peuvent passer par un ensemble d’états, et conserver un état une fois ce dernier défini. Pour obtenir des exemples de contrôles qui implémentent ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## Conventions et directives d'implémentation  
 Quand vous implémentez le modèle de contrôle Toggle, notez les conventions et recommandations suivantes :  
  
-   Les contrôles qui ne conservent pas l’état une fois ce dernier activé, par exemple les boutons, les boutons de barre d’outils et les liens hypertexte, doivent implémenter <xref:System.Windows.Automation.Provider.IInvokeProvider> à la place.  
  
-   Un contrôle doit parcourir <xref:System.Windows.Automation.ToggleState> dans l’ordre suivant : <xref:System.Windows.Automation.ToggleState>, <xref:System.Windows.Automation.ToggleState> et, si cela est pris en charge, <xref:System.Windows.Automation.ToggleState>.  
  
-   <xref:System.Windows.Automation.TogglePattern> ne fournit pas de méthode SetState\(newState\) en raison de problèmes liés à la définition directe d’une case à cocher à trois états sans parcourir sa séquence <xref:System.Windows.Automation.ToggleState> appropriée.  
  
-   Le contrôle de type RadioButton n’implémente pas <xref:System.Windows.Automation.Provider.IToggleProvider>, car il n’est pas capable de parcourir ses états valides.  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## Membres obligatoires pour IToggleProvider  
 Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d'<xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
|Membre obligatoire|Type de membre|Notes|  
|------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Propriété|None|  
  
 Ce modèle de contrôle n’est associé à aucun événement.  
  
<a name="Exceptions"></a>   
## Exceptions  
 Ce modèle de contrôle n’est associé à aucune exception.  
  
## Voir aussi  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [Get the Toggle State of a Check Box Using UI Automation](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)