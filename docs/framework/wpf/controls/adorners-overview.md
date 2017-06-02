---
title: "Vue d&#39;ensemble des ornements | Microsoft Docs"
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
  - "ornements (WPF), à propos des ornements"
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# Vue d&#39;ensemble des ornements
Les ornements sont un type spécial de <xref:System.Windows.FrameworkElement>, utilisés pour fournir des signaux visuels à un utilisateur.  Parmi les autres utilisations, les ornements peuvent être utilisés pour ajouter des handles fonctionnels aux éléments ou fournir des informations d'état à propos d'un contrôle.  
  
   
  
<a name="about_Adorners"></a>   
## À propos des ornements  
 Un <xref:System.Windows.Documents.Adorner> est un <xref:System.Windows.FrameworkElement> personnalisé lié à un <xref:System.Windows.UIElement>.  Les ornements sont restitués dans un <xref:System.Windows.Documents.AdornerLayer>, qui est une surface de rendu toujours située au dessus de l'élément ornementé ou une collection d'éléments ornementés.  Le rendu d'un ornement est indépendant du rendu de l'<xref:System.Windows.UIElement> auquel est lié l'ornement.  Un ornement est positionné en général par rapport à l'élément auquel il est lié, à l'aide des coordonnées 2D standard d'origine situées au coin supérieur gauche de l'élément ornementé.  
  
 Les applications courantes pour les ornements incluent :  
  
-   L'ajout de handles fonctionnels à un <xref:System.Windows.UIElement> qui permet à un utilisateur de manipuler l'élément d'une certaine façon \(redimensionner, faire pivoter, repositionner, etc.\).  
  
-   La fourniture d'une rétroaction visuelle pour indiquer différents états, ou en réponse à divers événements.  
  
-   La superposition de décorations visuelles sur un <xref:System.Windows.UIElement>.  
  
-   La masquage visuel ou le remplacement partiel ou complet d'un <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit une infrastructure de base pour ornementer des éléments visuels.  La table suivante répertorie les types principaux utilisés lors de l'ornementation d'objets, et leur but.  Plusieurs exemples d'utilisation suivent.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Une classe de base abstraite à partir de laquelle toutes les implémentations d'ornement concrètes héritent.|  
|<xref:System.Windows.Documents.AdornerLayer>|Une classe qui représente une couche de rendu pour le\(s\) ornements d'un ou plusieurs éléments ornementés.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Une classe qui permet d'associer une couche d'ornement à une collection d'éléments.|  
  
<a name="implement_custom_Adorner"></a>   
## Implémentation d'un ornement personnalisé  
 L'infrastructure des ornements fournie par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est prévue à l'origine pour prendre en charge la création d'ornements personnalisés.  Un ornement personnalisé est créé en implémentant une classe qui hérite de la classe abstraite <xref:System.Windows.Documents.Adorner>.  
  
> [!NOTE]
>  Le parent d'un <xref:System.Windows.Documents.Adorner> est la <xref:System.Windows.Documents.AdornerLayer> qui restitue l'<xref:System.Windows.Documents.Adorner>, pas l'élément qui est ornementé.  
  
 L'exemple suivant montre une classe qui implémente un ornement simple.  L'ornement d'exemple ornemente simplement les angles d'un <xref:System.Windows.UIElement> avec des cercles.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 L'image suivante montre le SimpleCircleAdorner appliqué à une <xref:System.Windows.Controls.TextBox>.  
  
 ![Exemple d'ornements : zone de texte ornée](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")  
  
<a name="rendering_behavior_for_Adorners"></a>   
## Rendu du comportement pour les ornements  
 Il est important de noter que les ornements n'incluent aucun comportement de rendu inhérent ; garantissant que le rendu d'un ornement est la responsabilité de l'implémenteur d'ornement.  Un moyen courant d'implémentation du comportement de rendu est de remplacer la méthode <xref:System.Windows.UIElement.OnRender%2A> et d'utiliser un ou plusieurs objets <xref:System.Windows.Media.DrawingContext> pour restituer les visuels de l'ornement en fonction des besoins \(comme illustré dans l'exemple ci\-dessous\).  
  
> [!NOTE]
>  Tout ce qui est placé dans la couche d'ornement est restitué au dessus de tous les styles que vous avez définis.  En d'autres termes, les ornements sont toujours visuellement en haut et ne peuvent pas être substitués à l'aide [de l'ordre de plan](GTMT).  
  
<a name="adorner_events_hittest"></a>   
## Événements et test de positionnement  
 Les ornements reçoivent des événements d'entrée comme n'importe quel autre <xref:System.Windows.FrameworkElement>.  Un ornement ayant toujours un [ordre de plan](GTMT) plus élevé que l'élément qu'il ornemente, l'ornement reçoit des événements d'entrée \(tel qu'un <xref:System.Windows.UIElement.Drop> ou <xref:System.Windows.UIElement.MouseMove>\) qui peuvent être prévus pour l'élément ornementé sous\-jacent.  Un ornement peut écouter certains événements d'entrée et les passer sur l'élément ornementé sous\-jacent en déclenchant à nouveau l'événement.  
  
 Pour permettre le test de positionnement direct d'éléments sous un ornement, définissez la propriété de test de positionnement <xref:System.Windows.UIElement.IsHitTestVisible%2A> à **false** sur l'ornement.  Pour plus d'informations sur les tests de positionnement, consultez  
  
 [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## Ornementer un UIElement unique  
 Pour lier un ornement à un <xref:System.Windows.UIElement> particulier, suivez les étapes ci\-dessous :  
  
1.  Appelez la méthode statique <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour obtenir un objet <xref:System.Windows.Documents.AdornerLayer> pour le <xref:System.Windows.UIElement> à orner.  <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> parcourt l'arborescence d'éléments visuels en commençant par le <xref:System.Windows.UIElement> spécifié et retourne la première couche d'ornement qu'il trouve.  \(Si aucune couche d'ornement n'est trouvée, la méthode retourne la valeur null.\)  
  
2.  Appelez la méthode <xref:System.Windows.Documents.AdornerLayer.Add%2A> pour lier l'ornement à la cible <xref:System.Windows.UIElement>.  
  
 L'exemple suivant lie un SimpleCircleAdorner \(illustré ci\-dessus\) à une <xref:System.Windows.Controls.TextBox> appelée *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  L'utilisation de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n'est pas prise en charge actuellement.  
  
<a name="adorn_children_panel"></a>   
## Ornementer les enfants d'un volet  
 Pour lier un ornement aux enfants d'un <xref:System.Windows.Controls.Panel>, suivez ces étapes :  
  
1.  Appelez la méthode `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour rechercher une couche d'ornement pour l'élément dont les enfants doivent être ornementés.  
  
2.  Énumérez les enfants de l'élément parent et appelez la méthode <xref:System.Windows.Documents.AdornerLayer.Add%2A> pour lier un ornement à chaque élément enfant.  
  
 L'exemple suivant lie un SimpleCircleAdorner \(montré ci\-dessus\) aux enfants d'un <xref:System.Windows.Controls.StackPanel> nommé *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## Voir aussi  
 <xref:System.Windows.Media.AdornerHitTestResult>   
 [Vue d'ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Vue d'ensemble des objets Drawing](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)