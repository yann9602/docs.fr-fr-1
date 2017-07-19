---
title: "Comment&#160;: g&#233;rer un &#233;v&#233;nement rout&#233; | Microsoft Docs"
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
  - "événements de propagation"
  - "événements routés, gérer"
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# Comment&#160;: g&#233;rer un &#233;v&#233;nement rout&#233;
Cet exemple illustre le fonctionnement des événements de [propagation](GTMT) et indique comment écrire un gestionnaire permettant de traiter les données des [événements routés](GTMT).  
  
## Exemple  
 Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les éléments sont organisés dans une [arborescence d'éléments](GTMT).  L'élément parent peut participer à la gestion des événements déclenchés initialement par les éléments enfants dans l'arborescence d'éléments.  Ceci est possible grâce au [routage d'événement](GTMT).  
  
 En règle générale, les événements routés respectent l'une des deux stratégies de routage : [propagation](GTMT) ou [tunneling](GTMT).  Cet exemple se concentre sur l'événement de [propagation](GTMT) et utilise l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=fullName> pour indiquer le fonctionnement du routage.  
  
 L'exemple suivant crée deux contrôles <xref:System.Windows.Controls.Button> et utilise la syntaxe d'attribut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour attacher un gestionnaire d'événements à un élément parent commun \(dans cet exemple, <xref:System.Windows.Controls.StackPanel>\).  Au lieu d'attacher un gestionnaire d'événements à chaque élément enfant <xref:System.Windows.Controls.Button>, l'exemple utilise la syntaxe d'attribut pour attacher le gestionnaire d'événements à l'élément parent <xref:System.Windows.Controls.StackPanel>.  Ce modèle de gestion des événements indique comment utiliser le routage d'événements afin de réduire le nombre d'éléments attachés à un gestionnaire.  Tous les événements de [propagation](GTMT) de chaque <xref:System.Windows.Controls.Button> passent par l'élément parent.  
  
 Sur l'élément parent <xref:System.Windows.Controls.StackPanel>, le nom de l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> spécifié comme attribut est partiellement qualifié en nommant la classe <xref:System.Windows.Controls.Button>.  La classe <xref:System.Windows.Controls.Button> est une classe dérivée <xref:System.Windows.Controls.Primitives.ButtonBase> dont la liste de membres comporte l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  Cette technique de qualification partielle permettant d'attacher un gestionnaire d'événements est nécessaire si l'événement géré n'existe pas dans la liste de membres de l'élément auquel le gestionnaire d'événements routés est attaché.  
  
 [!code-xml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 L'exemple suivant gère l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  L'exemple signale l'élément qui gère l'événement, ainsi que l'élément qui déclenche l'événement.  Le gestionnaire d'événements est exécuté lorsque l'utilisateur clique sur l'un des boutons.  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## Voir aussi  
 <xref:System.Windows.RoutedEvent>   
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)   
 [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)