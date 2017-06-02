---
title: "Implementing the UI Automation Transform Control Pattern | Microsoft Docs"
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
  - "control patterns, Transform"
  - "Transform control pattern"
  - "UI Automation, Transform control pattern"
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: 14
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 14
---
# Implementing the UI Automation Transform Control Pattern
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions et directives à respecter pour implémenter <xref:System.Windows.Automation.Provider.ITransformProvider>, notamment les informations sur les propriétés, les méthodes et les événements. Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.  
  
 Le modèle de contrôle <xref:System.Windows.Automation.TransformPattern> permet de prendre en charge des contrôles qui peuvent être déplacés, redimensionnés ou pivotés dans un espace à deux dimensions. Pour obtenir des exemples de contrôles implémentant ce modèle de contrôle, consultez [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## Conventions et directives d'implémentation  
 Quand vous implémentez le modèle de contrôle Transform, notez les conventions et recommandations suivantes :  
  
-   La prise en charge pour ce modèle de contrôle ne se limite pas aux objets sur le bureau. Ce modèle de contrôle doit également être pris en charge par les enfants d’un objet conteneur si les enfants peuvent être déplacés, redimensionnés et pivotés librement dans les limites du conteneur.  
  
-   Il n’est pas possible de déplacer, redimensionner ni pivoter un objet de manière à ce que son emplacement résultant à l’écran soit complètement en dehors des coordonnées de son conteneur et, par conséquent, inaccessible via le clavier et la souris \(par exemple, quand une fenêtre de niveau supérieur est déplacée hors de l’écran ou qu’un objet enfant est déplacé en dehors des limites de la fenêtre d’affichage du conteneur\). Dans ce cas, l’objet est placé le plus près possible des coordonnées d’écran demandées avec les coordonnées en haut et à gauche substituées de façon à être incluses dans les limites du conteneur.  
  
-   Pour les systèmes à plusieurs écrans, si un objet est déplacé, redimensionné ou pivoté complètement en dehors des coordonnées d’écran du bureau combiné, l’objet est placé sur le moniteur principal, aussi près que possible des coordonnées demandées.  
  
-   Tous les paramètres et valeurs de propriété sont absolus et indépendants des paramètres régionaux.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## Membres requis pour ITransformProvider  
 Les propriétés et méthodes suivantes sont nécessaires à l'implémentation d'<xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
|Membres nécessaires|Type de membre|Notes|  
|-------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Méthode|Aucun|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Méthode|None|  
  
 Ce modèle de contrôle n’est associé à aucun événement.  
  
<a name="Exceptions"></a>   
## Exceptions  
 Les fournisseurs doivent lever les exceptions suivantes.  
  
|Type d'exception|Condition|  
|----------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -   Si le <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> a la valeur false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -   Si le <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> a la valeur false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -   Si le <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> a la valeur false.|  
  
## Voir aussi  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)