---
title: "Impl&#233;mentation du mod&#232;le de contr&#244;le ScrollItem d’UI Automation | Microsoft Docs"
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
  - "modèles de contrôle, élément de défilement"
  - "Automation d’interface utilisateur, contrôle ScrollItem"
  - "ScrollItem (modèle de contrôle)"
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: 16
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 16
---
# Impl&#233;mentation du mod&#232;le de contr&#244;le ScrollItem d’UI Automation
> [!NOTE]
>  Cette documentation est destinée aux développeurs .NET Framework qui veulent utiliser managé [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes définies dans le <xref:System.Windows.Automation> espace de noms. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions de mise en œuvre et la <xref:System.Windows.Automation.Provider.IScrollItemProvider>, notamment des informations sur les propriétés, méthodes et événements. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le <xref:System.Windows.Automation.ScrollItemPattern> du modèle de contrôle est utilisé pour prendre en charge les contrôles enfants individuels de conteneurs qui implémentent <xref:System.Windows.Automation.Provider.IScrollProvider>. Ce modèle de contrôle agit comme un canal de communication entre un contrôle enfant et son conteneur pour garantir que le conteneur est en mesure de modifier le contenu (ou la zone) actuellement visible dans sa fenêtre d’affichage pour afficher le contrôle enfant. Pour obtenir des exemples de contrôles qui implémentent ce modèle de contrôle, consultez la page [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et directives d'implémentation  
 Quand vous implémentez le modèle de contrôle Scroll Item, notez les conventions et recommandations suivantes :  
  
-   Les éléments contenus dans un contrôle Window ou Canvas ne sont pas tenus d’implémenter l’interface IScrollItemProvider. Comme alternative, toutefois, ils doivent exposer un emplacement valide pour le <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Ainsi, une application cliente UI Automation utilise le <xref:System.Windows.Automation.ScrollPattern> méthodes de modèle dans le conteneur pour afficher l’élément enfant du contrôle.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Membres requis pour IScrollItemProvider  
 La méthode suivante est requise pour l’implémentation de l’interface IScrollProvider.  
  
|Membres nécessaires|Type de membre|Notes|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-(Méthode)|Aucun|  
  
 Ce modèle de contrôle n’est associé à aucune propriété ni à aucun événement.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Si un élément ne peut pas être l’objet d’un défilement dans la vue :<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Prise en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [Modèles de contrôle UI Automation pour les Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [Vue d’ensemble d’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)