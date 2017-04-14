---
title: "Comment&#160;: trier et grouper des donn&#233;es &#224; l&#39;aide d&#39;une vue en XAML | Microsoft Docs"
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
  - "liaison de données, regrouper des données dans des vues en XAML"
  - "liaison de données, trier des données dans des vues en XAML"
  - "regrouper des données dans des vues en XAML"
  - "trier des données dans des vues en XAML"
  - "vues, regrouper des données"
  - "vues, trier les données"
  - "XAML, regrouper des données dans des vues"
  - "XAML, trier des données dans des vues"
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: trier et grouper des donn&#233;es &#224; l&#39;aide d&#39;une vue en XAML
Cet exemple indique comment créer une vue d'une collecte de données en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Les vues tiennent compte des fonctionnalités de regroupement, de tri, de filtrage, et la notion d'un élément actuel.  
  
## Exemple  
 Dans l'exemple suivant, la ressource statique nommée *emplacements* est définie comme une collection d'objets *Emplacement*, dans laquelle chaque objet *Emplacement* se compose d'un nom de ville et d'état.  Le préfixe *src* est mappé à l'espace de noms où la source de données *Emplacements* est définie.  Le préfixe *scm* est mappé vers `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` et le préfixe *dat* est mappé vers `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 L'exemple suivant crée une vue de la collecte de données triée par nom de ville et groupée par état.  
  
 [!code-xml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 La vue peut alors être une source de liaison, comme dans l'exemple suivant :  
  
 [!code-xml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Pour les liaisons aux données XML définies dans une ressource <xref:System.Windows.Data.XmlDataProvider>, faites précéder le nom XML du symbole @.  
  
 [!code-xml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## Voir aussi  
 <xref:System.Windows.Data.CollectionViewSource>   
 [Obtenir la vue par défaut d'une collection de données](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)