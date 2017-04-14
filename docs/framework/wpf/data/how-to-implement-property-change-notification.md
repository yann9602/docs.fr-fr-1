---
title: "Comment&#160;: impl&#233;menter la notification des modifications de propri&#233;t&#233;s | Microsoft Docs"
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
  - "notifications de modifications"
  - "liaison de données, notifications de modifications de propriétés"
  - "notifications de modifications"
  - "propriétés, notifications de modifications"
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: impl&#233;menter la notification des modifications de propri&#233;t&#233;s
Pour prendre en charge la liaison <xref:System.Windows.Data.BindingMode> ou <xref:System.Windows.Data.BindingMode> permettant à vos propriétés [de cible de liaison](GTMT) de refléter automatiquement les modifications dynamiques de la [source de liaison](GTMT) \(par exemple, avoir le volet d'aperçu mis à jour automatiquement lorsque l'utilisateur modifie un formulaire\), votre classe doit fournir les notifications de modification de propriété appropriées.  Cet exemple indique comment créer une classe qui implémente <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## Exemple  
 Pour implémenter <xref:System.ComponentModel.INotifyPropertyChanged>, vous devez déclarer l'événement <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> et créer la méthode `OnPropertyChanged`.  Puis, pour chaque propriété pour laquelle vous souhaitez obtenir des notifications de modification, vous appelez `OnPropertyChanged` à chaque fois que la propriété est mise à jour.  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Pour consulter un exemple montrant comment la classe `Person` peut être utilisée pour prendre en charge la liaison <xref:System.Windows.Data.BindingMode>, consultez [Contrôler quand le texte TextBox met à jour la source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## Voir aussi  
 [Vue d'ensemble des sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)