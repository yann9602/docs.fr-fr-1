---
title: "Comment&#160;: rendre des donn&#233;es disponibles pour la liaison en XAML | Microsoft Docs"
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
  - "lier des données, rendre des données disponibles pour"
  - "liaison de données, rendre des données disponibles pour une liaison"
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: rendre des donn&#233;es disponibles pour la liaison en XAML
Cette rubrique aborde les différentes manières de rendre les données disponibles pour la liaison en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], en fonction des besoins de votre application.  
  
## Exemple  
 Si vous souhaitez effectuer une liaison sur un objet [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] à partir de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], une des méthodes vous permettant de rendre cet objet disponible pour la liaison est de le définir comme une ressource et de lui attribuer une `x:Key`.  Dans l'exemple suivant, vous avez un objet `Person` avec une propriété de type chaîne nommée `PersonName`.  L'objet `Person` est défini dans l'espace de noms appelé `SDKSample`.  
  
 [!code-xml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 Vous pouvez ensuite lier l'objet en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], comme illustré dans l'exemple suivant :  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 Vous pouvez également utiliser la classe <xref:System.Windows.Data.ObjectDataProvider>, comme dans l'exemple suivant.  
  
 [!code-xml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 Vous définissez la liaison de la même manière.  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 Dans cet exemple particulier, le résultat est le même : vous avez un <xref:System.Windows.Controls.TextBlock> avec le contenu de texte `Joe`.  Cependant, la classe <xref:System.Windows.Data.ObjectDataProvider> fournit une fonctionnalité telle que la possibilité d'effectuer une liaison sur le résultat d'une méthode.  Vous pouvez choisir d'utiliser la classe <xref:System.Windows.Data.ObjectDataProvider> si vous avez besoin de la fonctionnalité qu'elle fournit.  
  
 Toutefois, si vous effectuez une liaison à un objet déjà créé, vous devez définir le `DataContext` dans le code, comme dans l'exemple suivant.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Pour accéder aux données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pour la liaison en utilisant la classe <xref:System.Windows.Data.XmlDataProvider>, consultez [Effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  Pour accéder aux données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pour la liaison en utilisant la classe <xref:System.Windows.Data.ObjectDataProvider>, consultez [Effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Pour plus d'informations sur les différentes manières vous permettant de spécifier les données que vous liez, consultez [Spécifier la source de liaison](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).  Pour plus d'informations sur les types de données sur lesquelles vous pouvez effectuer une liaison, ou comment implémenter vos propres objets [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] pour la liaison, consultez [Vue d'ensemble des sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)