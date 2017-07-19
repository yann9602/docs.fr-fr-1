---
title: "Comment&#160;: sp&#233;cifier la source de liaison | Microsoft Docs"
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
  - "lier des données, sources de liaison"
  - "sources de liaison"
  - "liaison de données, source de liaison"
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: sp&#233;cifier la source de liaison
Dans la liaison de données, l'objet [de source de liaison](GTMT) fait référence à l'objet dont vous obtenez vos données.  Cette rubrique décrit les différentes manières de spécifier la [source de liaison](GTMT).  
  
## Exemple  
 Si vous liez plusieurs propriétés à une source commune, vous souhaitez utiliser la propriété `DataContext`, qui offre un moyen pratique d'établir une portée dans laquelle toutes les propriétés liées aux données héritent d'une source commune.  
  
 Dans l'exemple suivant, le contexte de données est établi à l'élément racine de l'application.  Cela permet à tous les éléments enfants d'hériter de ce contexte de données.  Les données pour la liaison viennent d'une classe de données personnalisée, `NetIncome`, référencée directement à travers un mappage et attribuée de la clé de ressource `incomeDataSource`.  
  
 [!code-xml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 L'exemple suivant illustre la définition de la classe `NetIncome`.  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  L'exemple précité instancie l'objet dans la balise et l'utilise comme une ressource.  Si vous souhaitez créer une liaison avec un objet qui a déjà été instancié dans le code, vous devez définir la propriété `DataContext` par programme.  Pour obtenir un exemple, consultez [Rendre des données disponibles pour la liaison en XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).  
  
 Ou bien, si vous souhaitez spécifier explicitement la source sur vos liaisons individuelles, vous disposez des options suivantes.  Celles\-ci ont priorité sur le contexte de données hérité.  
  
|Propriété|Description|  
|---------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Vous utilisez cette propriété pour définir la source sur l'instance d'un objet.  Si vous n'avez pas besoin des fonctionnalités d'établissement d'une portée dans laquelle plusieurs propriétés héritent du même contexte de données, vous pouvez utiliser la propriété <xref:System.Windows.Data.Binding.Source%2A> au lieu de la propriété `DataContext`.  Pour plus d'informations, consultez <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|C'est utile lorsque vous souhaitez spécifier la source relative à l'emplacement où se trouve votre [cible de liaison](GTMT).  Quelques scénarios courants où vous pouvez utiliser cette propriété : lorsque vous souhaitez lier une propriété de votre élément à une autre propriété du même élément ou si vous définissez une liaison dans un style ou un modèle.  Pour plus d'informations, consultez <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Vous spécifiez une chaîne qui représente l'élément sur lequel vous souhaitez effectuer la liaison.  C'est utile lorsque vous souhaitez créer une liaison avec la propriété d'un autre élément sur votre application.  Par exemple, si vous souhaitez utiliser un <xref:System.Windows.Controls.Slider> pour contrôler la hauteur d'un autre contrôle dans votre application, ou si vous voulez lier le <xref:System.Windows.Controls.ContentControl.Content%2A> de votre contrôle à la propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> de votre contrôle <xref:System.Windows.Controls.ListBox>.  Pour plus d'informations, consultez <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=fullName>   
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=fullName>   
 [Héritage de la valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des déclarations de liaison](../../../../docs/framework/wpf/data/binding-declarations-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)