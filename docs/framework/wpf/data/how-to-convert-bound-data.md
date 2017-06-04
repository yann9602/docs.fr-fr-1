---
title: "Comment&#160;: convertir des donn&#233;es li&#233;es | Microsoft Docs"
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
  - "lier des données, convertir des données liées"
  - "convertir, données liées"
  - "liaison de données, convertir des données liées"
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: convertir des donn&#233;es li&#233;es
Cet exemple montre comment convertir des données utilisées dans des liaisons.  
  
 Pour convertir des données pendant une liaison, vous devez créer une classe qui implémente l'interface <xref:System.Windows.Data.IValueConverter>, laquelle inclut les méthodes <xref:System.Windows.Data.IValueConverter.Convert%2A> et <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.  
  
## Exemple  
 L'exemple suivant illustre l'implémentation d'un convertisseur de date qui convertit la valeur de date qui lui est passée de manière à afficher uniquement l'année, le mois et le jour.  Lors de l'implémentation de l'interface <xref:System.Windows.Data.IValueConverter>, il est recommandé de décorer l'implémentation avec un attribut <xref:System.Windows.Data.ValueConversionAttribute> pour indiquer aux outils de développement quels sont les types de données impliqués dans la conversion, comme dans l'exemple suivant :  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Après avoir créé un convertisseur, vous pouvez l'ajouter en tant que ressource dans votre fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Dans l'exemple suivant, *src* correspond à l'espace de noms dans lequel est défini le *convertisseur de date*.  
  
 [!code-xml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Enfin, vous pouvez utiliser le convertisseur dans votre liaison à l'aide de la syntaxe suivante.  Dans l'exemple suivant, le contenu textuel de <xref:System.Windows.Controls.TextBlock> est lié à *StartDate*, qui est une propriété d'une source de données externe.  
  
 [!code-xml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Les ressources de style référencées dans l'exemple ci\-dessus sont définies dans une section de ressources qui n'est pas illustrée dans cette rubrique.  
  
## Voir aussi  
 [Implémenter la validation de la liaison](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)