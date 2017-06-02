---
title: "Comment&#160;: supprimer des liaisons | Microsoft Docs"
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
  - "liaisons, effacer"
  - "efffacer des liaisons"
  - "liaison de données, efffacer des liaisons"
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: supprimer des liaisons
Cet exemple montre comment supprimer les liaisons avec un objet.  
  
## Exemple  
 Pour supprimer une liaison d'une propriété individuelle sur un objet, appelez <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> comme indiqué dans l'exemple suivant.  L'exemple suivant supprime la liaison d'une <xref:System.Windows.Controls.TextBlock.TextProperty> de *mytext*, un objet <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 La suppression de liaison élimine la liaison de façon que la valeur de la [propriété de dépendance](GTMT) devienne ce qu'elle aurait été sans la liaison.  Cette valeur pourrait être une valeur par défaut, une valeur héritée ou une valeur d'une liaison de modèle de données.  
  
 Pour supprimer des liaisons de toutes les propriétés possibles sur un objet, utilisez <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## Voir aussi  
 <xref:System.Windows.Data.BindingOperations>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)