---
title: "Comment&#160;: effectuer une liaison &#224; une collection et afficher des informations bas&#233;es sur la s&#233;lection | Microsoft Docs"
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
  - "liaison de données, lier à des collections"
  - "liaison de données, créer des vues de collections de données"
  - "liaison de données, sélectionner des données pour des vues"
  - "collections de données, sélectionner des données pour des vues"
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: effectuer une liaison &#224; une collection et afficher des informations bas&#233;es sur la s&#233;lection
Dans un scénario maître\/détail simple, vous disposez d'un <xref:System.Windows.Controls.ItemsControl> lié aux données, tel qu'un <xref:System.Windows.Controls.ListBox>.  Selon la sélection de l'utilisateur, vous affichez davantage d'informations sur l'élément sélectionné.  Cet exemple indique comment implémenter ce scénario.  
  
## Exemple  
 Dans cet exemple, `People` est un <xref:System.Collections.ObjectModel.ObservableCollection%601> de la classe `Person`.  Cette classe `Person` contient trois propriétés : `FirstName`, `LastName` et `HomeTown`, de type `string`.  
  
 [!code-xml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 Le <xref:System.Windows.Controls.ContentControl> utilise le <xref:System.Windows.DataTemplate> suivant qui définit comment les informations d'un `Person` sont présentées :  
  
 [!code-xml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 La capture d'écran suivante illustre l'exemple.  <xref:System.Windows.Controls.ContentControl> affiche toutes les autres propriétés de la personne sélectionnée.  
  
 ![Liaison à une collection](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding\_CollectionBindingSample")  
  
 Les deux choses à remarquer dans cet exemple sont :  
  
1.  <xref:System.Windows.Controls.ListBox> et <xref:System.Windows.Controls.ContentControl> sont liés à la même source.  Les propriétés <xref:System.Windows.Data.Binding.Path%2A> des deux liaisons ne sont pas spécifiées car les deux contrôles créent une liaison à l'objet de collection tout entier.  
  
2.  Vous devez affecter la valeur `true` à la propriété <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> pour que cela se produise.  La définition de cette propriété garantit que l'élément sélectionné est toujours défini comme <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.  Ou bien, si <xref:System.Windows.Controls.ListBox> obtient ses données à partir de <xref:System.Windows.Data.CollectionViewSource>, celui\-ci synchronise automatiquement la sélection et la devise.  
  
 Notez que la classe `Person` remplace la méthode `ToString` de la façon suivante.  Par défaut, <xref:System.Windows.Controls.ListBox> appelle `ToString` et affiche une représentation sous forme de chaîne de chaque objet dans la collection liée.  C'est pourquoi chaque `Person` apparaît comme prénom dans le <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## Voir aussi  
 [Utiliser le modèle maître\/détail avec des données hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)   
 [Utiliser le modèle maître\/détail avec des données XML hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)