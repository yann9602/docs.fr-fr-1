---
title: "Impl&#233;mentation du mod&#232;le de contr&#244;le GridItem d’UI Automation | Microsoft Docs"
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
  - "modèles de contrôle GridItem"
  - "UI Automation (modèle de contrôle GridItem)"
  - "GridItem (modèle de contrôle)"
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
caps.latest.revision: 15
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 15
---
# Impl&#233;mentation du mod&#232;le de contr&#244;le GridItem d’UI Automation
> [!NOTE]
>  Cette documentation est destinée aux développeurs .NET Framework qui veulent utiliser managé [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes définies dans le <xref:System.Windows.Automation> espace de noms. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique présente les conventions de mise en œuvre et <xref:System.Windows.Automation.Provider.IGridItemProvider>, y compris des informations sur les propriétés. Des liens vers des références supplémentaires sont répertoriés à la fin de la vue d'ensemble.  
  
 Le <xref:System.Windows.Automation.GridItemPattern> du modèle de contrôle est utilisé pour prendre en charge les contrôles enfants individuels de conteneurs qui implémentent <xref:System.Windows.Automation.Provider.IGridProvider>. Pour obtenir des exemples de contrôles qui implémentent ce modèle de contrôle, consultez la page [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Conventions et directives d'implémentation  
 Lors de l’implémentation <xref:System.Windows.Automation.Provider.IGridProvider>, notez les conventions et instructions suivantes :  
  
-   Les coordonnées de grille ont une base zéro et la cellule supérieure gauche possède les coordonnées (0, 0).  
  
-   Cellules fusionnées communiqueront leurs <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> et <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> propriétés basées sur leur cellule d’ancrage sous-jacente, comme défini par le fournisseur UI Automation. En règle générale, il s’agit de la ligne la plus haute ou de la colonne la plus à gauche.  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> ne fournit pas de manipulation active de la grille, telles que la fusion ou le fractionnement des cellules.  
  
-   Contrôles qui implémentent <xref:System.Windows.Automation.Provider.IGridItemProvider> peut généralement être parcouru (autrement dit, un client UI Automation peut déplacer vers les contrôles adjacents) à l’aide du clavier.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Membres obligatoires pour IGridItemProvider  
 Les propriétés et méthodes suivantes sont requises pour implémenter <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Membres nécessaires|Type de membre|Notes|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Propriété|Aucun|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Propriété|None|  
  
 Ce modèle de contrôle n’est associé à aucune méthode ou aucun événement.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 Ce modèle de contrôle n’est associé à aucune exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Prise en charge des modèles de contrôle dans un fournisseur UI Automation](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [Modèles de contrôle UI Automation pour les Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [Implémenter le modèle de contrôle Grid d’UI Automation](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)   
 [Vue d’ensemble d’arborescence UI Automation](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)