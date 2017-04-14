---
title: "Comment&#160;: impl&#233;menter une propri&#233;t&#233; de d&#233;pendance | Microsoft Docs"
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
  - "propriétés de dépendance, sauvegarder des propriétés avec"
  - "propriétés, sauvegarder des propriétés de dépendance"
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: impl&#233;menter une propri&#233;t&#233; de d&#233;pendance
Cet exemple montre comment stocker une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] avec un champ <xref:System.Windows.DependencyProperty> et ainsi définir une [propriété de dépendance](GTMT).  Lorsque vous définissez vos propres propriétés et voulez qu'elles prennent en charge de nombreux aspects des fonctionnalités [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], telles que les styles, la liaison de données, l'héritage, l'animation et les valeurs par défaut, vous devez les implémenter en tant que [propriétés de dépendance](GTMT).  
  
## Exemple  
 L'exemple suivant enregistre tout d'abord une [propriété de dépendance](GTMT) en appelant la méthode <xref:System.Windows.DependencyProperty.Register%2A>.  Le nom du champ d'identificateur que vous utilisez pour stocker le nom et les caractéristiques de la [propriété de dépendance](GTMT) doit être <xref:System.Windows.DependencyProperty.Name%2A> que vous avez choisi pour la propriété de dépendance dans le cadre de l'appel <xref:System.Windows.DependencyProperty.Register%2A>, ajouté par la chaîne littérale `Property`.  Par exemple, si vous enregistrez une propriété de dépendance avec un <xref:System.Windows.DependencyProperty.Name%2A> de `Location`, le champ d'identificateur que vous définissez pour la propriété de dépendance doit être appelé `LocationProperty`.  
  
 Dans cet exemple, le nom de la [propriété de dépendance](GTMT) et de son accesseur [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] est `State`, le champ d'identificateur est `StateProperty`, le type de la propriété est <xref:System.Boolean> et le type qui enregistre la [propriété de dépendance](GTMT) est `MyStateControl`.  
  
 Si vous ne suivez pas ce modèle d'affectation de noms, les concepteurs risquent de ne pas signaler votre propriété correctement, tandis que certains aspects de l'application du style du système de propriétés pourraient avoir un comportement inattendu.  
  
 Vous pouvez également spécifier des métadonnées par défaut pour une [propriété de dépendance](GTMT).  Cet exemple enregistre la valeur par défaut `false` pour la [propriété de dépendance](GTMT) `State`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Pour plus d'informations sur l'implémentation d'une [propriété de dépendance](GTMT) et les raisons de cette implémentation, par opposition au simple stockage d'une propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] par un champ privé, consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## Voir aussi  
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)