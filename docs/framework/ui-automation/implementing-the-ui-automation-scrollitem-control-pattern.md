---
title: "Implémentation du modèle de contrôle ScrollItem d'UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ef089e72c3b8dd089db5022ea1808cee98c27ecd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Implémentation du modèle de contrôle ScrollItem d’UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions de mise en œuvre et la <xref:System.Windows.Automation.Provider.IScrollItemProvider>, notamment des informations sur les propriétés, méthodes et événements. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le <xref:System.Windows.Automation.ScrollItemPattern> modèle de contrôle est utilisé pour prendre en charge les contrôles enfants individuels des conteneurs qui implémentent <xref:System.Windows.Automation.Provider.IScrollProvider>. Ce modèle de contrôle agit comme un canal de communication entre un contrôle enfant et son conteneur pour garantir que le conteneur est en mesure de modifier le contenu (ou la zone) actuellement visible dans sa fenêtre d’affichage pour afficher le contrôle enfant. Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et recommandations en matière d'implémentation  
 Quand vous implémentez le modèle de contrôle Scroll Item, notez les conventions et recommandations suivantes :  
  
-   Les éléments contenus dans un contrôle Window ou Canvas ne sont pas tenus d’implémenter l’interface IScrollItemProvider. En guise d’alternative, toutefois, ils doivent exposer un emplacement valide pour le <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Ainsi, une application du client UI Automation à utiliser le <xref:System.Windows.Automation.ScrollPattern> sur le conteneur pour afficher l’élément enfant, les méthodes de modèle de contrôle.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Membres requis pour IScrollItemProvider  
 La méthode suivante est requise pour l’implémentation de l’interface IScrollProvider.  
  
|Membres requis|Type de membre|Notes|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-(Méthode)|Aucun.|  
  
 Ce modèle de contrôle n’est associé à aucune propriété ni à aucun événement.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Si un élément ne peut pas être l’objet d’un défilement dans la vue :<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Prendre en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Modèles de contrôle UI Automation pour les clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Présentation de l’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
