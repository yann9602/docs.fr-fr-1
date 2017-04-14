---
title: "Comment&#160;: ajouter un type propri&#233;taire d&#39;une propri&#233;t&#233; de d&#233;pendance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "classes, ajouter en tant que propriétaires de propriétés de dépendance"
  - "propriétés de dépendance, ajouter des classes en tant que propriétaires de"
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: ajouter un type propri&#233;taire d&#39;une propri&#233;t&#233; de d&#233;pendance
Cet exemple montre comment ajouter une classe sous la forme d'un propriétaire d'une propriété de dépendance inscrite pour un type différent.  En procédant ainsi, le lecteur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et le système de propriétés peuvent reconnaître la classe en tant que propriétaire supplémentaire de la propriété.  L'ajout comme propriétaire permet éventuellement d'ajouter une classe pour fournir des métadonnées de type.  
  
 Dans l'exemple suivant, `StateProperty` est une propriété inscrite par la classe `MyStateControl`.  La classe `UnrelatedStateControl` s'ajoute comme un propriétaire de la `StateProperty` à l'aide de la méthode <xref:System.Windows.DependencyProperty.AddOwner%2A>, spécifiquement en utilisant la signature qui tient compte des nouvelles métadonnées de la propriété de dépendance telles qu'elles existent dans le type d'ajout.  Notez que vous devez fournir des accesseurs [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] pour la propriété semblables à ceux de l'exemple [Implémenter une propriété de dépendance](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md), et réexposer l'identificateur de propriété de dépendance dans la classe ajoutée comme propriétaire.  
  
 Sans wrappers, la propriété de dépendance continuerait de fonctionner du point de vue de l'accès par programme en utilisant <xref:System.Windows.DependencyObject.GetValue%2A> ou <xref:System.Windows.DependencyObject.SetValue%2A>.  Mais vous voulez en fait placer parallèlement ce comportement de système de propriétés avec les wrappers de propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  Les wrappers simplifient la définition de propriété de dépendance par programme et permettent de définir les propriétés comme attributs [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Pour savoir comment remplacer les métadonnées par défaut, consultez [Substituer les métadonnées d'une propriété de dépendance](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).  
  
## Exemple  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## Voir aussi  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)