---
title: "Implémentation du modèle de contrôle TableItem d'UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5861ab24627f9b78cd20f97fcdb1b1b3d681991a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implémentation du modèle de contrôle TableItem d’UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions de mise en œuvre et <xref:System.Windows.Automation.Provider.ITableItemProvider>, y compris des informations sur les événements et propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.  
  
 Le <xref:System.Windows.Automation.TableItemPattern> modèle de contrôle est utilisé pour prendre en charge les contrôles enfants des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.ITableProvider>. Accès aux fonctionnalités de cellules individuelles est fourni par l’implémentation simultanée requise de <xref:System.Windows.Automation.Provider.IGridItemProvider>. Ce modèle de contrôle est analogue à <xref:System.Windows.Automation.Provider.IGridItemProvider> à la différence que tout contrôle implémentant <xref:System.Windows.Automation.Provider.ITableItemProvider> doit exposer par programmation la relation entre la cellule individuelle et ses informations de ligne et de colonne. Pour obtenir des exemples de contrôles qui implémentent ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et recommandations en matière d'implémentation  
  
-   Pour les fonctionnalités de grille associées, consultez [implémentation du modèle de contrôle UI Automation GridItem](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>Membres obligatoires pour ITableItemProvider  
  
|Membre obligatoire|Type de membre|Notes|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Méthode|Aucune|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Méthode|None|  
  
 Ce modèle de contrôle n’est associé à aucune propriété ni à aucun événement.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Ce modèle de contrôle n’est associé à aucune exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du modèles contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Prise en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Modèles de contrôle UI Automation pour les Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implémentation du modèle de contrôle Table UI Automation](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [Implémentation du modèle de contrôle GridItem d’UI Automation](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [Vue d’ensemble d’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
