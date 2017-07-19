---
title: "Implementing the UI Automation MultipleView Control Pattern | Microsoft Docs"
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
  - "UI Automation, MultipleView control pattern"
  - "MultipleView control pattern"
  - "control patterns, MultipleView"
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
caps.latest.revision: 15
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 15
---
# Implementing the UI Automation MultipleView Control Pattern
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, notamment des informations sur les événements et les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.MultipleViewPattern> permet de prendre en charge des contrôles qui fournissent plusieurs représentations du même ensemble d’informations ou de contrôles enfants, et permettent de basculer entre elles.  
  
 Les exemples de contrôles qui peuvent présenter plusieurs vues incluent la vue Liste \(dont le contenu peut apparaître sous forme de miniatures, vignettes, icônes ou détails\), les graphiques [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] \(secteur, ligne, barre, valeur d’une cellule avec une formule\), les documents [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] \(affichage normal, mode web, mode Impression, mode Lecture, mode Plan\), le calendrier [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] \(année, mois, semaine, jour\) et les apparences [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)]. Les vues prises en charge sont déterminées par le développeur de contrôle et sont spécifiques à chaque contrôle.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## Conventions et directives d'implémentation  
 Quand vous implémentez le modèle de contrôle Multiple View, notez les conventions et recommandations suivantes :  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider> doit également être implémenté sur un conteneur qui gère la vue actuelle s’il est différent d’un contrôle qui fournit la vue actuelle. Par exemple, l’Explorateur Windows contient un contrôle List pour le contenu du dossier actuel, tandis que la vue du contrôle est gérée à partir de l’application de l’Explorateur Windows.  
  
-   Un contrôle qui est en mesure de trier son contenu n’est pas censé prendre en charge plusieurs vues.  
  
-   La collection de vues doit être identique sur l’ensemble des instances.  
  
-   Les noms des vues doivent pouvoir être utilisés dans le cadre de la synthèse vocale, de l’écriture en Braille et dans d’autres applications lisibles par l’utilisateur.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## Membres requis pour IMultipleViewProvider  
 Les propriétés et méthodes suivantes sont requises pour implémenter IMultipleViewProvider.  
  
|Membres nécessaires|Type de membre|Notes|  
|-------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Méthode|None|  
  
 Aucun événement n’est associé à ce modèle de contrôle.  
  
<a name="Exceptions"></a>   
## Exceptions  
 Le fournisseur doit lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|----------------------|---------------|  
|<xref:System.ArgumentException>|Quand la méthode <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> est appelée avec un paramètre qui n’est pas membre de la collection de vues prises en charge.|  
  
## Voir aussi  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)