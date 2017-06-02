---
title: "Comment&#160;: utiliser la classe FontSizeConverter | Microsoft Docs"
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
  - "objets FontSizeConverter"
  - "typographie, objets FontSizeConverter"
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: utiliser la classe FontSizeConverter
## Exemple  
 Cet exemple montre comment créer une instance de <xref:System.Windows.FontSizeConverter> et l'utiliser pour modifier une taille de police.  
  
 L'exemple définit une méthode personnalisée appelée `changeSize` qui convertit le contenu d'un <xref:System.Windows.Controls.ListBoxItem>, comme défini dans un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] séparé, en une instance de <xref:System.Double>, et par la suite en une <xref:System.String>.  Cette méthode passe le <xref:System.Windows.Controls.ListBoxItem> à un objet <xref:System.Windows.FontSizeConverter> qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d'un <xref:System.Windows.Controls.ListBoxItem> en une instance de <xref:System.Double>.  Cette valeur est ensuite retournée comme valeur de la propriété <xref:System.Windows.Controls.TextBlock.FontSize%2A> de l'élément <xref:System.Windows.Controls.TextBlock>.  
  
 Cet exemple définit également une deuxième méthode personnalisée qui est appelée `changeFamily`.  Cette méthode convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> du <xref:System.Windows.Controls.ListBoxItem> en <xref:System.String>, puis passe cette valeur à la propriété <xref:System.Windows.Controls.TextBlock.FontFamily%2A> de l'élément <xref:System.Windows.Controls.TextBlock>.  
  
 Cet exemple ne s'exécute pas.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## Voir aussi  
 <xref:System.Windows.FontSizeConverter>