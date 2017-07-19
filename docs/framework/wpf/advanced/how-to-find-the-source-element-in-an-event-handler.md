---
title: "Comment&#160;: rechercher l&#39;&#233;l&#233;ment source dans un gestionnaire d&#39;&#233;v&#233;nements | Microsoft Docs"
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
  - "gestionnaires d'événements, rechercher un élément source dans"
  - "élément source dans des gestionnaires d'événements"
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: rechercher l&#39;&#233;l&#233;ment source dans un gestionnaire d&#39;&#233;v&#233;nements
Cet exemple montre comment rechercher l'élément source dans un gestionnaire d'événements.  
  
## Exemple  
 L'exemple suivant présente un gestionnaire d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click> déclaré dans un fichier code\-behind.  Lorsqu'un utilisateur clique sur le bouton auquel est relié le gestionnaire, celui\-ci modifie une valeur de propriété.  Le code du gestionnaire utilise la propriété <xref:System.Windows.RoutedEventArgs.Source%2A> des données d'événement routées renseignée dans les arguments d'événement pour modifier la valeur de la  propriété <xref:System.Windows.FrameworkElement.Width%2A> sur l'élément <xref:System.Windows.RoutedEventArgs.Source%2A>.  
  
 [!code-xml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## Voir aussi  
 <xref:System.Windows.RoutedEventArgs>   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)