---
title: "Comment&#160;: animer une propri&#233;t&#233; &#224; l&#39;aide d&#39;un storyboard | Microsoft Docs"
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
  - "animation, Animations"
  - "Animations, animation"
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: animer une propri&#233;t&#233; &#224; l&#39;aide d&#39;un storyboard
Cet exemple montre comment utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour animer des propriétés.  Pour animer une propriété en utilisant un <xref:System.Windows.Media.Animation.Storyboard>, créez une animation pour chaque propriété que vous souhaitez animer et créez également un <xref:System.Windows.Media.Animation.Storyboard> pour contenir les animations.  
  
 Le type de propriété détermine le type d'animation à utiliser.  Par exemple, pour animer une propriété qui accepte des valeurs <xref:System.Double>, utilisez un <xref:System.Windows.Media.Animation.DoubleAnimation>.  Les [propriétés attachées](GTMT) <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> spécifient l'objet et la propriété auxquels l'animation est appliquée.  
  
 Pour commencer un storyboard en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], utilisez une action <xref:System.Windows.Media.Animation.BeginStoryboard> et un <xref:System.Windows.EventTrigger>.  Le <xref:System.Windows.EventTrigger> commence l'action <xref:System.Windows.Media.Animation.BeginStoryboard> lorsque l'événement spécifié par sa propriété <xref:System.Windows.EventTrigger.RoutedEvent%2A> se produit.  L'action <xref:System.Windows.Media.Animation.BeginStoryboard> démarre le <xref:System.Windows.Media.Animation.Storyboard>.  
  
 L'exemple suivant utilise des objets <xref:System.Windows.Media.Animation.Storyboard> pour animer deux contrôles <xref:System.Windows.Controls.Button>.  Pour modifier la taille du premier bouton, sa <xref:System.Windows.FrameworkElement.Width%2A> est animée.  Pour modifier la couleur du deuxième bouton, la propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A> du <xref:System.Windows.Media.SolidColorBrush> est utilisée pour définir le <xref:System.Windows.Controls.Control.Background%2A> du bouton animé.  
  
## Exemple  
 [!code-xml[AnimatePropertyStoryboards#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  Bien que les animations puissent cibler à la fois un objet <xref:System.Windows.FrameworkElement>, tel qu'un <xref:System.Windows.Controls.Control> ou <xref:System.Windows.Controls.Panel>, et un objet <xref:System.Windows.Freezable>, tel qu'un <xref:System.Windows.Media.Brush> ou <xref:System.Windows.Media.Transform>, seuls les éléments d'infrastructure ont une propriété <xref:System.Windows.FrameworkElement.Name%2A>.  Pour assigner un nom à un Freezable afin qu'il puisse être ciblé par une animation, utilisez [x:Name, directive](../../../../docs/framework/xaml-services/x-name-directive.md), comme indiqué par l'exemple précédent.  
  
 Si vous utilisez du code, vous devez créer un <xref:System.Windows.NameScope> pour un <xref:System.Windows.FrameworkElement> et enregistrer les noms des objets à animer avec ce <xref:System.Windows.FrameworkElement>.  Pour démarrer les animations dans le code, utilisez une action <xref:System.Windows.Media.Animation.BeginStoryboard> avec un <xref:System.Windows.EventTrigger>.  Vous pouvez éventuellement utiliser un gestionnaire d'événements et la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> de <xref:System.Windows.Media.Animation.Storyboard>.  L'exemple suivant illustre l'utilisation de la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Pour plus d'informations sur l'animation et les tables de montage séquentiel, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Si vous utilisez du code, vous n'êtes pas limité à l'utilisation d'objets <xref:System.Windows.Media.Animation.Storyboard> pour animer des propriétés.  Pour plus d'informations et d'exemples, consultez [Animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md) et [Animer une propriété à l'aide d'un AnimationClock](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).