---
title: "Comment&#160;: cr&#233;er et effectuer une liaison &#224; un ObservableCollection | Microsoft Docs"
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
  - "classes, ObservableCollection"
  - "liaison de données, ObservableCollection (classe)"
  - "notifications"
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: cr&#233;er et effectuer une liaison &#224; un ObservableCollection
Cet exemple montre comment créer et effectuer une liaison à une collection qui dérive de la classe <xref:System.Collections.ObjectModel.ObservableCollection%601>, qui est une classe de collection fournissant des notifications lors de l'ajout ou de la suppression d'éléments.  
  
## Exemple  
 L'exemple suivant montre l'implémentation d'une collection `NameList` :  
  
 [!code-csharp[MultiBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[MultiBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameList.vb#1)]  
  
 Vous pouvez rendre la collection disponible pour la liaison de la même manière que pour les autres objets [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], comme décrit dans [Rendre des données disponibles pour la liaison en XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).  Par exemple, vous pouvez instancier la collection en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et spécifier la collection en tant que ressource, comme cela est illustré comme suit :  
  
 [!code-xml[MultiBinding#OCHowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#ochowto)]  
[!code-xml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
  
 Vous pouvez ensuite lier à la collection :  
  
 [!code-xml[MultiBinding#MultiBindingListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindinglistbox)]  
  
 La définition de `NameItemTemplate` n'est pas affichée ici.  
  
> [!NOTE]
>  Les objets de votre collection doivent répondre aux exigences décrites dans [Vue d'ensemble des sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md).  En particulier, si vous utilisez <xref:System.Windows.Data.BindingMode> ou <xref:System.Windows.Data.BindingMode> \(par exemple, vous souhaitez que votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se mette à jour lorsque les propriétés sources changent dynamiquement\), vous devez implémenter un mécanisme de notification de modification de propriété adapté comme l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Pour plus d'informations, consultez la section Liaison à des collections dans [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## Voir aussi  
 [Trier des données dans une vue](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [Filtrer les données d'une vue](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [Trier et grouper des données à l'aide d'une vue en XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)