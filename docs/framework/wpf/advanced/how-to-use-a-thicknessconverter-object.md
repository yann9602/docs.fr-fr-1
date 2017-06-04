---
title: "Comment&#160;: utiliser un objet ThicknessConverter | Microsoft Docs"
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
  - "épaisseur d'une bordure"
  - "objets ThicknessConverter"
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: utiliser un objet ThicknessConverter
## Exemple  
 Cet exemple montre comment créer une instance de <xref:System.Windows.ThicknessConverter> et l'utiliser pour modifier l'épaisseur d'une bordure.  
  
 L'exemple définit une méthode personnalisée appelée `changeThickness` ; cette méthode convertit d'abord le contenu d'un <xref:System.Windows.Controls.ListBoxItem>, comme défini dans un fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] séparé, en une instance de <xref:System.Windows.Thickness>, et convertit par la suite le contenu en <xref:System.String>.  Cette méthode passe le <xref:System.Windows.Controls.ListBoxItem> à un objet <xref:System.Windows.ThicknessConverter> qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d'un <xref:System.Windows.Controls.ListBoxItem> en une instance de <xref:System.Windows.Thickness>.  Cette valeur est ensuite retournée comme valeur de la propriété <xref:System.Windows.Controls.Border.BorderThickness%2A> de la <xref:System.Windows.Controls.Border>.  
  
 Cet exemple ne s'exécute pas.  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Thickness>   
 <xref:System.Windows.ThicknessConverter>   
 <xref:System.Windows.Controls.Border>   
 [How to: Change the Margin Property](http://msdn.microsoft.com/fr-fr/8a313efd-5f99-4097-b4c1-8fa49d8379a2)   
 [How to: Convert a ListBoxItem to a new Data Type](http://msdn.microsoft.com/fr-fr/7a080b88-184e-4b27-bb61-d42bafba9727)   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)