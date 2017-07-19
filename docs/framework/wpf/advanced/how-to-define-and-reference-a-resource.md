---
title: "Comment&#160;: d&#233;finir et r&#233;f&#233;rencer une ressource | Microsoft Docs"
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
  - "définir des ressources"
  - "référencer des ressources"
  - "ressources, définition"
  - "ressources, référencer"
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: d&#233;finir et r&#233;f&#233;rencer une ressource
Cet exemple montre comment définir une ressource et la référencer à l'aide d'un attribut en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## Exemple  
 L'exemple suivant définit deux types of ressources : une ressource <xref:System.Windows.Media.SolidColorBrush> et plusieurs ressources <xref:System.Windows.Style>.  La ressource <xref:System.Windows.Media.SolidColorBrush> `MyBrush` est utilisée pour fournir la valeur de plusieurs propriétés qui prennent chacune une valeur de type <xref:System.Windows.Media.Brush>.  Les ressources <xref:System.Windows.Style> `PageBackground`, `TitleText` et `Label` ciblent chacune un type de contrôle particulier.  Les styles définissent diverses propriétés sur les contrôles ciblés lorsque cette ressource de style est référencée par une clé de ressource et utilisée pour définir la propriété <xref:System.Windows.FrameworkElement.Style%2A> de plusieurs éléments de contrôle spécifiques définis en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Notez que l'une des propriétés des accesseurs Set de propriétés du style `Label` fait également référence à la ressource `MyBrush` définie précédemment.  C'est une technique courante, mais il est important de se rappeler que les ressources sont analysées et entrées dans un dictionnaire de ressources dans l'ordre où elles sont fournies.  Les ressources sont également demandées dans l'ordre où elles se trouvent dans le dictionnaire si vous utilisez l'[StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) pour les référencer à partir d'une autre ressource.  Assurez\-vous que toute ressource que vous référencez a été définie dans la collection de ressources avant l'endroit où la ressource est demandée.  Si nécessaire, vous pouvez contourner l'ordre strict de création des références de ressources en utilisant une [DynamicResource, extension de balisage](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) pour référencer la ressource au moment de l'exécution, mais vous devez savoir que la technique DynamicResource a des conséquences sur les performances.  Pour plus d'informations, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## Voir aussi  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)