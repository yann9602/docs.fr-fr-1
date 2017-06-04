---
title: "Comment&#160;: cr&#233;er une liaison simple | Microsoft Docs"
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
  - "liaison de données, créer des liaisons simples"
  - "liaison simple, créer"
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: cr&#233;er une liaison simple
Cet exemple vous indique comment créer une <xref:System.Windows.Data.Binding> simple.  
  
## Exemple  
 Dans cet exemple, vous avez un objet `Person` avec une propriété de type chaîne nommée `PersonName`.  L'objet `Person` est défini dans l'espace de noms appelé `SDKSample`.  
  
 L'exemple suivant instancie l'objet `Person` avec une valeur de propriété `PersonName` de `Joe`.  Cela s'effectue dans la section `Resources` et un `x:Key` est attribué.  
  
 [!code-xml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
[!code-xml[SimpleBinding#EndWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#endwindow)]  
  
 Pour créer une liaison avec la propriété `PersonName`, vous devez effectuer les opérations suivantes :  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 En conséquence, le <xref:System.Windows.Controls.TextBlock> apparaît avec la valeur "Joe."  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)