---
title: "Utilisation d&#39;objets DrawingVisual | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DrawingVisual (objets dans la couche visuelle)"
  - "couche visuelle, objets DrawingVisual"
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Utilisation d&#39;objets DrawingVisual
Cette rubrique fournit une vue d'ensemble de l'utilisation d'objets <xref:System.Windows.Media.DrawingVisual> dans la couche visuelle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Cette rubrique contient les sections suivantes.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [Objet DrawingVisual](#drawing_visual_object)  
  
-   [Conteneur hôte DrawingVisual](#drawingvisual_host_container)  
  
-   [Création d'objets DrawingVisual](#creating_drawingvisual_objects)  
  
-   [Création de substitutions pour des membres FrameworkElement](#creating_overrides)  
  
-   [Fourniture de la prise en charge des tests de positionnement](#providing_hit_testing_support)  
  
-   [Rubriques connexes](#seeAlsoToggle)  
  
<a name="drawingvisual_object"></a>   
## Objet DrawingVisual  
 <xref:System.Windows.Media.DrawingVisual> est une classe de dessin légère utilisée pour le rendu des formes, des images ou du texte.  Cette classe est considérée comme légère parce qu'elle ne fournit pas la disposition ou la gestion d'événements, ce qui améliore ses performances.  Pour cette raison, les objets de ce type sont idéaux pour les arrière\-plans et les images clipart.  
  
<a name="drawingvisual_host_container"></a>   
## Conteneur hôte DrawingVisual  
 Pour pouvoir utiliser des objets <xref:System.Windows.Media.DrawingVisual>, vous devez créer un conteneur hôte pour les objets.  L'objet conteneur hôte doit être dérivé de la classe <xref:System.Windows.FrameworkElement>, qui fournit la disposition et la gestion des événements que la classe <xref:System.Windows.Media.DrawingVisual> ne prend pas en charge.  L'objet conteneur hôte n'affiche aucune propriété visible, car il est principalement conçu pour contenir des objets enfants.  Toutefois, la propriété <xref:System.Windows.UIElement.Visibility%2A> du conteneur hôte doit avoir la valeur <xref:System.Windows.Visibility>, sinon, aucun de ses éléments enfants n'est visible.  
  
 Lorsque vous créez un objet conteneur hôte pour des objets visuels, vous devez stocker les références des objets visuels dans un <xref:System.Windows.Media.VisualCollection>.  Utilisez la méthode <xref:System.Windows.Media.VisualCollection.Add%2A> pour ajouter un objet visuel au conteneur hôte.  Dans l'exemple suivant, un objet conteneur hôte est créé et trois objets visuels sont ajoutés à <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Pour obtenir l'exemple de code complet duquel l'exemple de code précédent a été extrait, consultez [Test de positionnement à l'aide de DrawingVisuals, exemple](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## Création d'objets DrawingVisual  
 Lorsque vous créez un objet <xref:System.Windows.Media.DrawingVisual>, celui\-ci ne comporte aucun contenu de dessin.  Vous pouvez ajouter du texte, des graphiques ou du contenu d'image en récupérant le <xref:System.Windows.Media.DrawingContext> de l'objet et en dessinant dedans.  Un <xref:System.Windows.Media.DrawingContext> est retourné en appelant la méthode <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> d'un objet <xref:System.Windows.Media.DrawingVisual>.  
  
 Pour dessiner un rectangle dans <xref:System.Windows.Media.DrawingContext>, utilisez la méthode <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> de l'objet <xref:System.Windows.Media.DrawingContext>.  Il existe des méthodes similaires permettant de dessiner d'autres types de contenu.  Après avoir dessiné le contenu dans <xref:System.Windows.Media.DrawingContext>, appelez la méthode <xref:System.Windows.Media.DrawingContext.Close%2A> pour fermer <xref:System.Windows.Media.DrawingContext> et conserver le contenu.  
  
 Dans l'exemple suivant, un objet <xref:System.Windows.Media.DrawingVisual> est créé et un rectangle est dessiné dans <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## Création de substitutions pour des membres FrameworkElement  
 L'objet conteneur hôte est chargé de gérer sa collection d'objets visuels.  Pour ce faire, le conteneur hôte doit implémenter des substitutions de membres pour la classe <xref:System.Windows.FrameworkElement> dérivée.  
  
 La liste suivante décrit les deux membres que vous devez substituer :  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A> : retourne un enfant au niveau de l'index spécifié à partir de la collection d'éléments enfants.  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A> : obtient le nombre d'éléments enfants visuels dans cet élément.  
  
 Dans l'exemple suivant, des substitutions pour les deux membres <xref:System.Windows.FrameworkElement> sont implémentées.  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## Fourniture de la prise en charge des tests de positionnement  
 L'objet conteneur hôte peut fournir la gestion des événements même s'il n'affiche aucune propriété visible. Toutefois, sa propriété <xref:System.Windows.UIElement.Visibility%2A> doit avoir la valeur <xref:System.Windows.Visibility>.  Vous pouvez ainsi créer une routine de gestion des événements pour le conteneur hôte qui peut intercepter les événements de souris, comme le relâchement du bouton gauche de la souris.  La routine de gestion des événements peut ensuite implémenter les tests de positionnement en appelant la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  Le paramètre <xref:System.Windows.Media.HitTestResultCallback> de la méthode fait référence à une procédure définie par l'utilisateur que vous pouvez utiliser pour déterminer l'action résultante d'un test de positionnement.  
  
 Dans l'exemple suivant, la prise en charge des tests de positionnement est implémentée pour l'objet conteneur hôte et ses enfants.  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## Voir aussi  
 <xref:System.Windows.Media.DrawingVisual>   
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>   
 [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)