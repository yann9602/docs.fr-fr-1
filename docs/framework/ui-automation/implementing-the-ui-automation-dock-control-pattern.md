---
title: "Implémentation du modèle de contrôle Dock d'UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 68c3dcdb1d8f15f312dea40ae59a3b1a4736c484
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implémentation du modèle de contrôle Dock d’UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IDockProvider>, notamment des informations sur les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.DockPattern> est utilisé pour exposer les propriétés de l’ancrage d’un contrôle dans un conteneur d’ancrage. Un conteneur d’ancrage est un contrôle qui vous permet de réorganiser des éléments enfants horizontalement et verticalement, les uns par rapport aux autres. Pour obtenir des exemples de contrôles qui implémentent ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Conteneur d’ancrage avec deux enfants ancrés. ] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Exemple d’ancrage de Visual Studio où la fenêtre « Affichage de classes » est DockPosition.Right et la fenêtre « Liste d’erreurs » est DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et recommandations en matière d'implémentation  
 Lorsque vous implémentez le modèle de contrôle Dock, notez les conventions et recommandations suivantes :  
  
-   <xref:System.Windows.Automation.Provider.IDockProvider> n’expose aucune propriété du conteneur d’ancrage ni aucune propriété des contrôles qui sont ancrés de façon à être adjacents au contrôle actuel dans le conteneur d’ancrage.  
  
-   Les contrôles sont ancrés les uns par rapport aux autres selon leur ordre de plan actuel ; plus leur positionnement dans l’ordre de plan est haut, plus ils sont placés loin du bord spécifié du conteneur d’ancrage.  
  
-   Si le conteneur d’ancrage est redimensionné, tout contrôle ancré dans le conteneur est repositionné sur le même bord que celui auquel il était ancré à l’origine. Les contrôles ancrés sont également redimensionnés pour remplir tout l’espace du conteneur d’après le comportement d’ancrage de leur <xref:System.Windows.Automation.DockPosition>. Par exemple, si <xref:System.Windows.Automation.DockPosition.Top> est spécifié, les côtés gauche et droit du contrôle sont développés pour remplir l’espace disponible. Si <xref:System.Windows.Automation.DockPosition.Fill> est spécifié, les quatre côtés du contrôle sont développés pour remplir l’espace disponible.  
  
-   Sur un système à écrans multiples, les contrôles doivent être ancrés au côté gauche ou droit de l’écran actif. Si ce n’est pas possible, ils doivent être ancrés au côté gauche de l’écran le plus à gauche ou au côté droit de l’écran le plus à droite.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Membres requis pour IDockProvider  
 Les propriétés et méthodes suivantes sont requises pour implémenter l’interface IDockProvider.  
  
|Membres requis|Type de membre|Remarques|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Propriété|Aucune|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Méthode|Aucune|  
  
 Ce modèle de contrôle n’est associé aucun événement.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> -Lorsqu’un contrôle n’est pas en mesure d’exécuter le style d’ancrage demandé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du modèles contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Prise en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Modèles de contrôle UI Automation pour les Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Vue d’ensemble d’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
