---
title: "Comment&#160;: cr&#233;er une liaison dans du code | Microsoft Docs"
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
  - "lier des données, créer"
  - "liaison de données, créer"
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# Comment&#160;: cr&#233;er une liaison dans du code
Cet exemple indique comment créer et définir un <xref:System.Windows.Data.Binding> dans le code.  
  
## Exemple  
 Les classes <xref:System.Windows.FrameworkElement> et <xref:System.Windows.FrameworkContentElement> exposent toutes deux une méthode `SetBinding`.  Si vous liez un élément qui hérite de l'une ou l'autre de ces classes, vous pouvez appeler la méthode <xref:System.Windows.FrameworkElement.SetBinding%2A> directement.  
  
 L'exemple suivant crée une classe nommée `MyData`, qui contient une propriété nommée `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 L'exemple suivant indique comment créer un objet de liaison pour définir la source de liaison.  L'exemple utilise <xref:System.Windows.FrameworkElement.SetBinding%2A> pour lier la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> de `myText` \(qui est un contrôle <xref:System.Windows.Controls.TextBlock>\) à `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Pour obtenir l'exemple de code complet, consultez [Code\-only Binding Sample](http://msdn.microsoft.com/fr-fr/764aaf0b-2216-4941-9548-9c98da18d1a6).  
  
 Au lieu d'appeler <xref:System.Windows.FrameworkElement.SetBinding%2A>, vous pouvez utiliser la méthode statique <xref:System.Windows.Data.BindingOperations.SetBinding%2A> de la classe <xref:System.Windows.Data.BindingOperations>.  L'exemple suivant appelle <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=fullName> au lieu de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=fullName> pour lier `myText` à `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)