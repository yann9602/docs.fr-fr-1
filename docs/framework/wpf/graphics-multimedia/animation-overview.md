---
title: "Vue d&#39;ensemble de l&#39;animation | Microsoft Docs"
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
  - "Animations (WPF), des animations"
  - "animations (WPF), vue d’ensemble"
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
caps.latest.revision: 73
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 73
---
# Vue d&#39;ensemble de l&#39;animation
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un ensemble puissant de fonctionnalités graphiques et la disposition qui vous permettent de créer des interfaces utilisateur attrayantes et des documents attrayants. L’animation peut rendre une interface utilisateur attrayante encore plus spectaculaire et conviviale. En seulement animer une couleur d’arrière-plan ou en appliquant une animation <xref:System.Windows.Media.Transform>, vous pouvez créer des transitions d’écran impressionnantes ou fournir des aides visuelles utiles.  
  
 Cette présentation fournit une introduction à la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animation et le système de minuterie. Il se concentre sur l’animation de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objets à l’aide de tables de montage séquentiel.  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>Présentation des Animations  
 L’animation est une illusion créée en parcourant rapidement une série d’images, chacune légèrement différentes de la dernière. Le cerveau perçoit le groupe d’images comme une seule scène qui change. Dans un film, cette illusion est créée à l’aide de caméras qui enregistrent plusieurs photos, ou frames, chaque seconde. Lorsque les images sont lues par un projecteur, le public voit une image en mouvement.  
  
 Animation sur un ordinateur est similaire. Par exemple, un programme qui dessine un rectangle disparaisse en fondu peut fonctionner comme suit.  
  
-   Le programme crée un minuteur.  
  
-   Le programme vérifie la minuterie à intervalles définis pour voir combien de temps s’est écoulé.  
  
-   Chaque fois que le programme vérifie la minuterie, il calcule la valeur actuelle d’opacité du rectangle selon le temps écoulé.  
  
-   Ensuite, le programme met à jour le rectangle avec la nouvelle valeur et redessine.  
  
 Antérieures à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] les développeurs devaient créer et gérer leurs propres systèmes de minuterie ou utiliser des bibliothèques personnalisées spéciales.                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]inclut un système de minutage efficace exposé via du code managé et [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et qui est profondément intégré à la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework.                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]animation facilite l’animation de contrôles et autres objets graphiques.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]gère toutes les tâches en arrière-plan pour gérer un système de minuterie et pour redessiner l’écran efficacement. Il fournit les classes de synchronisation qui vous permettent de vous concentrer sur les effets que vous souhaitez créer, au lieu de la mécanique de la réalisation de ces effets.                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]facilite également créer vos propres animations en exposant les classes de base d’animation à partir de laquelle vos classes peuvent hériter, pour produire des animations personnalisées. Ces animations personnalisées récupèrent les avantages de performance des classes d’animation standard.  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>Système d’Animation de propriétés de WPF  
 Si vous comprenez certains des principaux concepts concernant le système de minuterie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animations peuvent être plus faciles à utiliser. Plus important est que, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], animer des objets en appliquant une animation à leurs propriétés individuelles. Par exemple, pour développer un élément d’infrastructure, vous animez sa <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés. Pour qu’un objet disparaisse en fondu, vous animez sa <xref:System.Windows.UIElement.Opacity%2A> propriété.  
  
 Pour une propriété disposent de fonctionnalités d’animation, il doit respecter les trois conditions suivantes :  
  
-   Il doit être une propriété de dépendance.  
  
-   Il doit appartenir à une classe qui hérite de <xref:System.Windows.DependencyObject> et implémente la <xref:System.Windows.Media.Animation.IAnimatable> interface.  
  
-   Un type d’animation compatible doit être disponible. (Si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’en fournit pas, vous pouvez créer vos propres. Consultez le [vue d’ensemble des Animations personnalisées](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).)  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]contient de nombreux objets qui ont <xref:System.Windows.Media.Animation.IAnimatable> propriétés. Les contrôles tels que <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.TabControl>et également <xref:System.Windows.Controls.Panel> et <xref:System.Windows.Shapes.Shape> objets héritent de <xref:System.Windows.DependencyObject>. La plupart de leurs propriétés sont des propriétés de dépendance.  
  
 Vous pouvez utiliser des animations presque n’importe où, y compris dans les styles et modèles de contrôle. Animations n’ont pas à être visuelles ; Vous pouvez animer des objets qui ne font pas partie de l’interface utilisateur s’ils répondent aux critères décrits dans cette section.  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Exemple : Créer un fondu élément  
 Cet exemple montre comment utiliser un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animation pour animer la valeur d’une propriété de dépendance. Il utilise un <xref:System.Windows.Media.Animation.DoubleAnimation>, qui est un type d’animation qui génère <xref:System.Double> pour animer les valeurs le <xref:System.Windows.UIElement.Opacity%2A> propriété d’un <xref:System.Windows.Shapes.Rectangle>. Par conséquent, le <xref:System.Windows.Shapes.Rectangle> apparaît et l’affichage disparaît.  
  
 La première partie de l’exemple crée un <xref:System.Windows.Shapes.Rectangle> élément. Les étapes suivantes montrent comment créer une animation et l’appliquer à du rectangle <xref:System.Windows.UIElement.Opacity%2A> propriété.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Shapes.Rectangle> élément dans une <xref:System.Windows.Controls.StackPanel> en XAML.  
  
 [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Shapes.Rectangle> élément dans une <xref:System.Windows.Controls.StackPanel> dans le code.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>Partie 1 : Créer un objet DoubleAnimation  
 Une façon de faire apparaître et disparaître un élément est d’animer sa <xref:System.Windows.UIElement.Opacity%2A> propriété. Étant donné que la <xref:System.Windows.UIElement.Opacity%2A> propriété est de type <xref:System.Double>, vous avez besoin d’une animation qui produit des valeurs de type double. A <xref:System.Windows.Media.Animation.DoubleAnimation> est de ce type. A <xref:System.Windows.Media.Animation.DoubleAnimation> crée une transition entre deux valeurs double. Pour spécifier sa valeur initiale, vous définissez son <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété. Pour spécifier sa valeur finale, définissez sa <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété.  
  
1.  Une valeur d’opacité de `1.0` rend l’objet totalement opaque et une valeur d’opacité de `0.0` rend totalement invisible. To make the animation transition from                                  `1.0` to                                  `0.0` you set its                                  <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> property to                                  `1.0` and its                                  <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> property to                                  `0.0`. L’exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.DoubleAnimation> en XAML.  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     L’exemple suivant montre comment créer un <xref:System.Windows.Media.Animation.DoubleAnimation> dans le code.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2.  Ensuite, vous devez spécifier un <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> d’une animation spécifie le temps nécessaire pour passer de sa valeur initiale à sa valeur de destination. L’exemple suivant montre comment définir le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> à cinq secondes en XAML.  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     L’exemple suivant montre comment définir le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> à cinq secondes dans le code.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3.  Le code précédent montrait une animation qui effectue la transition du `1.0` à `0.0`, ce qui provoque l’élément cible progressivement de complètement opaque à complètement invisible. Pour que l’élément réapparaisse en fondu après elle disparaît, définissez la <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriétés de l’animation à `true`. Pour répéter l’animation indéfiniment, définissez son <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. L’exemple suivant montre comment définir le <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> et <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriétés en XAML.  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     L’exemple suivant montre comment définir le <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> et <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriétés dans le code.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>Partie 2 : Créer une table de montage séquentiel  
 Pour appliquer une animation à un objet, vous créez un <xref:System.Windows.Media.Animation.Storyboard> et utiliser le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> jointes propriétés pour spécifier l’objet et la propriété à animer.  
  
1.  Créer le <xref:System.Windows.Media.Animation.Storyboard> et ajoutez-y l’animation en tant qu’enfant. L’exemple suivant montre comment créer le <xref:System.Windows.Media.Animation.Storyboard> en XAML.  
  
     <!-- TODO: review snippet reference [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]  -->  
  
     Pour créer le <xref:System.Windows.Media.Animation.Storyboard> dans le code, déclarez un <xref:System.Windows.Media.Animation.Storyboard> variable au niveau de la classe.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     Puis initialisez le <xref:System.Windows.Media.Animation.Storyboard> et ajoutez-y l’animation en tant qu’enfant.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2.  Le <xref:System.Windows.Media.Animation.Storyboard> doit savoir où appliquer l’animation. Utilisez le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName> propriété attachée pour spécifier l’objet à animer. L’exemple suivant montre comment définir le nom cible de la <xref:System.Windows.Media.Animation.DoubleAnimation> à `MyRectangle` en XAML.  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     L’exemple suivant montre comment définir le nom cible de la <xref:System.Windows.Media.Animation.DoubleAnimation> à `MyRectangle` dans le code.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3.  Utilisez le <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> propriété attachée pour spécifier la propriété à animer. L’exemple suivant montre comment l’animation est configurée pour cibler la <xref:System.Windows.UIElement.Opacity%2A> propriété de la <xref:System.Windows.Shapes.Rectangle> en XAML.  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     L’exemple suivant montre comment l’animation est configurée pour cibler la <xref:System.Windows.UIElement.Opacity%2A> propriété de la <xref:System.Windows.Shapes.Rectangle> dans le code.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 Pour plus d’informations sur <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> syntaxe et pour obtenir des exemples supplémentaires, consultez le [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Étape 3 (XAML) : Associer la table de montage séquentiel avec un déclencheur  
 Le moyen le plus simple d’appliquer et de démarrer un <xref:System.Windows.Media.Animation.Storyboard> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consiste à utiliser un déclencheur d’événement.                          Cette section indique comment associer le <xref:System.Windows.Media.Animation.Storyboard> avec un déclencheur en XAML.  
  
1.  Créer un <xref:System.Windows.Media.Animation.BeginStoryboard> objet et lui associer votre table de montage séquentiel. A <xref:System.Windows.Media.Animation.BeginStoryboard> est un type de <xref:System.Windows.TriggerAction> qui s’applique et démarre un <xref:System.Windows.Media.Animation.Storyboard>.  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2.  Créer un <xref:System.Windows.EventTrigger> et ajoutez le <xref:System.Windows.Media.Animation.BeginStoryboard> à son <xref:System.Windows.EventTrigger.Actions%2A> collection. Définir le <xref:System.Windows.EventTrigger.RoutedEvent%2A> propriété de la <xref:System.Windows.EventTrigger> à l’événement routé que vous souhaitez démarrer la <xref:System.Windows.Media.Animation.Storyboard>. (Pour plus d’informations sur les événements routés, consultez le [vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).)  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3.  Ajouter la <xref:System.Windows.EventTrigger> à la <xref:System.Windows.FrameworkElement.Triggers%2A> collection du Rectangle.  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Étape 3 (Code) : Associer la table de montage séquentiel avec un gestionnaire d’événements  
 Le moyen le plus simple d’appliquer et de démarrer un <xref:System.Windows.Media.Animation.Storyboard> dans le code est d’utiliser un gestionnaire d’événements. Cette section indique comment associer le <xref:System.Windows.Media.Animation.Storyboard> avec un gestionnaire d’événements dans le code.  
  
1.  Inscrivez-vous à la <xref:System.Windows.FrameworkElement.Loaded> événement du rectangle.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2.  Déclarez le Gestionnaire d’événements. Dans le Gestionnaire d’événements, utilisez la <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> méthode à appliquer la table de montage séquentiel.  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>Exemple complet  
 Le code suivant créer un rectangle qui permette le fondu et en XAML.  
  
 [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 Le code suivant créer un rectangle qui permette le fondu et dans le code.  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>Types d’animations  
 Étant donné que les animations génèrent des valeurs de propriété, différents types d’animation existent pour différents types de propriété. Pour animer une propriété qui accepte un <xref:System.Double>, tels que les <xref:System.Windows.FrameworkElement.Width%2A> propriété d’un élément, utilisez une animation qui produit des <xref:System.Double> valeurs. Pour animer une propriété qui accepte un <xref:System.Windows.Point>, utilisez une animation qui produit des <xref:System.Windows.Point> valeurs et ainsi de suite. En raison du nombre de différents types de propriété, il existe plusieurs classes d’animations dans le <xref:System.Windows.Media.Animation> espace de noms. Heureusement, ils suivent une convention d’appellation stricte qui facilite la différenciation :  
  
-   \<                         *Type*> Animation  
  
     Appelée « From/To/By » ou « basic » animation, ces animent entre une valeur de début et de destination, ou en ajoutant une valeur de décalage à sa valeur initiale.  
  
    -   Pour spécifier une valeur de départ, définissez la propriété à partir de l’animation.  
  
    -   Pour spécifier une valeur finale, définissez la propriété To de l’animation.  
  
    -   Pour spécifier une valeur de décalage, définissez la propriété By de l’animation.  
  
     Les exemples de cette vue d’ensemble utilisent ces animations car elles sont le plus simple à utiliser. Animations From/To/By sont décrites en détail dans la vue d’ensemble des Animations de From/To/By.  
  
-   \<                         *Type*> AnimationUsingKeyFrames  
  
     Animations d’image clé sont plus puissantes que les animations From/To/By car vous pouvez spécifier n’importe quel nombre de valeurs cibles et même contrôler leur méthode d’interpolation. Certains types ne peuvent être animés qu’avec des animations d’image clé. Animations d’image clé sont décrites en détail dans les [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   \<                         *Type*> AnimationUsingPath  
  
     Animations de tracés permettent d’utiliser un tracé géométrique pour produire des valeurs animées.  
  
-   \<                         *Type*> AnimationBase  
  
     Classe abstraite qui, lorsque vous l’implémentez, anime un <> \</> *Type*> valeur. Cette classe sert de classe de base pour <> \</> *Type*> Animation et <> \</> *Type*> AnimationUsingKeyFrames classes. Vous devez traiter directement avec ces classes uniquement si vous souhaitez créer vos propres animations personnalisées. Sinon, utilisez un <> \</> *Type*> Animation ou KeyFrame<>*Type*> Animation.  
  
 Dans la plupart des cas, vous souhaiterez utiliser le <> \</> *Type*> classes d’Animation, telles que <xref:System.Windows.Media.Animation.DoubleAnimation> et <xref:System.Windows.Media.Animation.ColorAnimation>.  
  
 Le tableau suivant montre plusieurs types d’animations courants et certaines propriétés avec lesquels ils sont utilisés.  
  
|Type de propriété|Animation de base (From/To/By) correspondante|Animation d’image clé correspondante|Animation de tracé correspondante|Exemple d’utilisation|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Aucune|Animate the                                  <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a                                  <xref:System.Windows.Media.SolidColorBrush> or a                                  <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animate the                                  <xref:System.Windows.FrameworkElement.Width%2A> of a                                  <xref:System.Windows.Controls.DockPanel> or the                                  <xref:System.Windows.FrameworkElement.Height%2A> of a                                  <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Animer le <xref:System.Windows.Media.EllipseGeometry.Center%2A> position d’un <xref:System.Windows.Media.EllipseGeometry>.|  
|<xref:System.String>|Aucune|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Aucune|Animate the                                  <xref:System.Windows.Controls.TextBlock.Text%2A> of a                                  <xref:System.Windows.Controls.TextBlock> or the                                  <xref:System.Windows.Controls.ContentControl.Content%2A> of a                                  <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>Les animations sont des chronologies  
 Tous les types d’animations héritent de la <xref:System.Windows.Media.Animation.Timeline> classe ; par conséquent, toutes les animations sont des types de chronologies spécialisés. A <xref:System.Windows.Media.Animation.Timeline> définit un segment de temps. Vous pouvez spécifier le *des comportements de minutage* d’une chronologie : sa <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, nombre de fois où il est répétée et même la rapidité d’y progresse.  
  
 Car une animation est une <xref:System.Windows.Media.Animation.Timeline>, elle représente également un segment de temps. Une animation calcule également les valeurs de sortie pendant sa progression via son segment de temps spécifié (ou <xref:System.Windows.Media.Animation.Timeline.Duration%2A>). En tant que l’animation progresse, ou « joue », il met à jour la propriété qui lui est associée.  
  
 Trois propriétés de minutage les plus utilisées sont <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, et <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.  
  
#### <a name="the-duration-property"></a>La propriété Duration  
 Comme mentionné précédemment, une chronologie représente un segment de temps. La longueur de ce segment est déterminée par le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de la chronologie, qui est généralement spécifiée en utilisant un <xref:System.Windows.Duration.TimeSpan%2A> valeur. Lorsqu’une chronologie atteint la fin de sa durée, elle a terminé une itération.  
  
 Une animation utilise sa <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriété pour déterminer sa valeur actuelle. Si vous ne spécifiez pas un <xref:System.Windows.Media.Animation.Timeline.Duration%2A> valeur pour une animation, il utilise 1 seconde, ce qui est la valeur par défaut.  
  
 La syntaxe suivante montre une version simplifiée de la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribut syntaxe pour le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriété.  
  
||  
|-|  
|*hours* `:` *minutes* `:` *seconds*|  
  
 Le tableau suivant montre plusieurs <xref:System.Windows.Duration> paramètres et leurs valeurs correspondantes.  
  
|Paramètre|Valeur de résultat|  
|-------------|---------------------|  
|0:0:5.5|5,5 secondes.|  
|0:30:5.5|30 minutes et 5,5 secondes.|  
|1:30:5.5|1 heure, 30 minutes, et 5.5 secondes.|  
  
 Une façon de spécifier un <xref:System.Windows.Duration> dans le code est d’utiliser le <xref:System.TimeSpan.FromSeconds%2A> pour créer un <xref:System.TimeSpan>, ensuite déclarer une nouvelle <xref:System.Windows.Duration> qui à l’aide de la structure <xref:System.TimeSpan>.  
  
 Pour plus d’informations sur <xref:System.Windows.Duration> la version complète et valeurs [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] syntaxe, consultez le <xref:System.Windows.Duration> structure.  
  
#### <a name="autoreverse"></a>AutoReverse  
 Le <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriété spécifie si une chronologie repart en arrière après avoir atteint la fin de son <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Si vous définissez cette propriété d’animation `true`, l’animation recommence après avoir atteint la fin de son <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, en commençant par sa valeur finale à sa valeur de départ. Par défaut, cette propriété est `false`.  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 Le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriété indique combien de fois une chronologie est lu. Par défaut, les chronologies ont un nombre d’itérations de `1.0`, ce qui signifie qu’ils jouent une fois et ne se répètent pas du tout.  
  
 Pour plus d’informations sur ces propriétés et d’autres, consultez le [vue d’ensemble des comportements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>Application d’une Animation à une propriété  
 Les sections précédentes décrivent les différents types d’animations et leurs propriétés de minutage. Cette section montre comment appliquer l’animation à la propriété que vous souhaitez animer.                  <xref:System.Windows.Media.Animation.Storyboard> objets fournissent un moyen d’appliquer des animations aux propriétés. A <xref:System.Windows.Media.Animation.Storyboard> est un *chronologie de conteneur* qui fournit des informations de ciblage pour les animations qu’il contient.  
  
### <a name="targeting-objects-and-properties"></a>Ciblage des objets et propriétés  
 Le <xref:System.Windows.Media.Animation.Storyboard> classe fournit le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> propriétés jointes. En définissant ces propriétés sur une animation, vous demandez à l’animation à animer. Toutefois, avant une animation peut cibler un objet, l’objet doit généralement être étant donné un nom.  
  
 Affectation d’un nom à un <xref:System.Windows.FrameworkElement> diffère de l’affectation d’un nom à un <xref:System.Windows.Freezable> objet. La plupart des contrôles et des panneaux est des éléments d’infrastructure ; Toutefois, les objets purement graphiques, tels que les pinceaux, les transformations et les géométries, sont des objets freezable. Si vous ne savez pas si un type est un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.Freezable>, reportez-vous à la **hiérarchie d’héritage** section de la documentation de référence.  
  
-   Pour rendre un <xref:System.Windows.FrameworkElement> une cible d’animation, vous lui donner un nom en définissant sa <xref:System.Windows.FrameworkElement.Name%2A> propriété. Dans le code, vous devez également utiliser le <xref:System.Windows.FrameworkElement.RegisterName%2A> méthode pour inscrire le nom de l’élément avec la page à laquelle il appartient.  
  
-   Pour rendre un <xref:System.Windows.Freezable> une cible d’animation dans l’objet [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez la [x : nom de la Directive](../../../../docs/framework/xaml-services/x-name-directive.md) pour lui attribuer un nom. Dans le code, utilisez simplement le <xref:System.Windows.FrameworkElement.RegisterName%2A> méthode pour enregistrer l’objet avec la page à laquelle il appartient.  
  
 Les sections qui suivent fournissent un exemple de nom d’un élément dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et le code. Pour obtenir des informations plus détaillées sur les noms et le ciblage, voir la [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="applying-and-starting-storyboards"></a>Application et démarrage des Storyboards  
 Pour démarrer une animation dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], associez-la à un <xref:System.Windows.EventTrigger>. Un <xref:System.Windows.EventTrigger> est un objet qui décrit les actions à entreprendre lorsqu’un événement spécifié se produit. L’une de ces actions peut être un <xref:System.Windows.Media.Animation.BeginStoryboard> action, ce qui vous permet de démarrer votre table de montage séquentiel. Déclencheurs d’événements sont un concept similaire aux gestionnaires d’événements car ils vous permettent de spécifier la façon dont votre application répond à un événement particulier. Contrairement aux gestionnaires d’événements, les déclencheurs d’événements peuvent être entièrement décrits dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; aucun code n’est requise.  
  
 Pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> dans le code, vous pouvez utiliser un <xref:System.Windows.EventTrigger> ou utilisez la <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> procédé de la <xref:System.Windows.Media.Animation.Storyboard> classe.  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>Contrôler un Storyboard de façon interactive  
 L’exemple précédent montrait comment démarrer un <xref:System.Windows.Media.Animation.Storyboard> lorsqu’un événement se produit. Vous pouvez contrôler également interactivement une <xref:System.Windows.Media.Animation.Storyboard> après son démarrage : vous pouvez suspendre, reprendre, arrêter, avancer à sa période de remplissage, rechercher et supprimer les <xref:System.Windows.Media.Animation.Storyboard>. Pour plus d’informations et un exemple qui montre comment contrôler de manière interactive un <xref:System.Windows.Media.Animation.Storyboard>, consultez la [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>Que se passe-t-il après la fin d’une Animation ?  
 Le <xref:System.Windows.Media.Animation.FillBehavior> propriété spécifie le comportement d’une chronologie lorsqu’elle se termine. Par défaut, une chronologie démarre <xref:System.Windows.Media.Animation.ClockState> lorsqu’elle se termine. Une animation <xref:System.Windows.Media.Animation.ClockState> conserve sa valeur finale.  
  
 Le <xref:System.Windows.Media.Animation.DoubleAnimation> dans l’exemple précédent ne se termine pas, car son <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> est définie sur <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>. L’exemple suivant anime un rectangle avec une animation semblable. Contrairement à l’exemple précédent, le <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> et <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriétés de cette animation conservent leurs valeurs par défaut. Par conséquent, l’animation passe de 1 à 0 en cinq secondes et s’arrête.  
  
 [!code-xml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 Étant donné que son <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> n’a pas été modifié à partir de sa valeur par défaut, qui est <xref:System.Windows.Media.Animation.FillBehavior>, l’animation conserve sa dernière valeur, c'est-à-dire 0, lorsqu’elle se termine. Par conséquent, le <xref:System.Windows.UIElement.Opacity%2A> du rectangle reste à 0 après l’animation se termine. Si vous définissez la <xref:System.Windows.UIElement.Opacity%2A> du rectangle à une autre valeur, votre code semble n’avoir aucun effet, car l’animation affectera toujours la <xref:System.Windows.UIElement.Opacity%2A> propriété.  
  
 Une façon de reprendre le contrôle d’une propriété animée dans le code est d’utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> (méthode) et de spécifier null pour le <xref:System.Windows.Media.Animation.AnimationTimeline> paramètre. Pour plus d’informations et un exemple, consultez [définir une propriété après l’animation avec un Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
 Notez que, bien que la définition d’une valeur de propriété a une <xref:System.Windows.Media.Animation.ClockState> ou <xref:System.Windows.Media.Animation.ClockState> animation semble n’avoir aucun effet, la valeur de propriété ne change pas. Pour plus d’informations, consultez la [Animation and Timing System Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>Liaison de données et animation  
 La plupart des propriétés d’animation peuvent être liées aux données ou animées ; par exemple, vous pouvez animer le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriétés d’un <xref:System.Windows.Media.Animation.DoubleAnimation>. Toutefois, en raison du mode de fonctionne du système de minuterie, données animations dépendant ou animées ne se comportent pas comme les autres données liées ou animés des objets. Pour comprendre leur comportement, vous pour devez comprendre ce que signifie appliquer une animation à une propriété.  
  
 Consultez l’exemple dans la section précédente qui montrait comment animer le <xref:System.Windows.UIElement.Opacity%2A> d’un rectangle. Lorsque le rectangle dans l’exemple précédent est chargé, son déclencheur d’événements applique le <xref:System.Windows.Media.Animation.Storyboard>. Le système de minuterie crée une copie de la <xref:System.Windows.Media.Animation.Storyboard> et son animation. Ces copies sont figées (en lecture seule) et <xref:System.Windows.Media.Animation.Clock> objets sont créés à partir de ceux-ci. Ces horloges effectuent le travail réel de l’animation des propriétés ciblées.  
  
 Le système de minuterie crée une horloge pour le <xref:System.Windows.Media.Animation.DoubleAnimation> et s’applique à l’objet et la propriété qui est spécifiée par le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> de la <xref:System.Windows.Media.Animation.DoubleAnimation>. Dans ce cas, le système de minuterie applique l’horloge à la <xref:System.Windows.UIElement.Opacity%2A> propriété de l’objet appelé « MyRectangle ».  
  
 Bien qu’une horloge est également créée pour le <xref:System.Windows.Media.Animation.Storyboard>, l’horloge n’est pas appliqué à toutes les propriétés. Son but est de contrôler son horloge enfant, l’horloge qui est créé pour le <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Pour une animation refléter les modifications d’animation ou de liaison de données, son horloge doit être régénérée. Horloges ne sont pas régénérées automatiquement pour vous. Pour qu’une animation reflète les modifications, appliquez sa table de montage séquentiel à l’aide un <xref:System.Windows.Media.Animation.BeginStoryboard> ou <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> méthode. Lorsque vous utilisez une des ces méthodes, l’animation redémarre. Dans le code, vous pouvez utiliser la <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> retour de méthode pour déplacer la table de montage séquentiel à sa position précédente.  
  
 Pour un exemple de données lié à l’animation, consultez [Key Spline Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160011).                  Pour plus d’informations sur le fonctionnement du système d’animation et le minutage, consultez [Animation and Timing System Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>Autres méthodes d’animation  
 Les exemples de cette vue d’ensemble montrent comment animer à l’aide de tables de montage séquentiel. Lorsque vous utilisez du code, vous pouvez animer de plusieurs autres façons. Pour plus d’informations, consultez la [Property Animation Techniques Overview](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>Exemples d’animation  
 Les exemples suivants peuvent vous aider à démarrer l’ajout d’une animation à vos applications.  
  
-   [À partir de, à et par des valeurs cible une Animation, exemple](http://go.microsoft.com/fwlink/?LinkID=159988)  
  
     Présente les paramètres de différents From/To/By.  
  
-   [Comportement de minutage d’animation exemple](http://go.microsoft.com/fwlink/?LinkID=159970)  
  
     Montre les différentes façons, vous pouvez contrôler le comportement de minutage d’une animation. Cet exemple également montre comment lier aux données d’une animation, la valeur de destination.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Animation et le minutage de vue d’ensemble du système](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)|Décrit comment le système de minuterie utilise le <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock> classes qui vous permettent de créer des animations.|  
|[Animation trucs et astuces](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)|Répertorie les conseils utiles pour résoudre les problèmes d’animation, tels que les performances.|  
|[Vue d’ensemble des Animations personnalisées](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)|Décrit comment étendre le système d’animation avec des images clés, des classes d’animation ou des rappels d’image par image.|  
|Vue d'ensemble des animations From/To/By|Décrit comment créer une animation qui effectue la transition entre deux valeurs.|  
|[Vue d’ensemble des Animations d’image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)|Décrit comment créer une animation avec plusieurs valeurs cibles, y compris la possibilité de contrôler la méthode d’interpolation.|  
|[Fonctions d’accélération](../../../../docs/framework/wpf/graphics-multimedia/easing-functions.md)|Explique comment appliquer des formules mathématiques à vos animations pour obtenir un comportement réaliste, tel que rebondissent.|  
|[Vue d’ensemble des Animations de chemin d’accès](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)|Décrit comment déplacer ou faire pivoter un objet sur un tracé complexe.|  
|[Propriété Animation Techniques Overview.](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)|Décrit des animations de propriété à l’aide de tables de montage séquentiel, animations locales, horloges et des animations image par image.|  
|[Vue d’ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)|Décrit comment utiliser les storyboards avec plusieurs chronologies pour créer des animations complexes.|  
|[Vue d’ensemble des comportements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)|Décrit la <xref:System.Windows.Media.Animation.Timeline> types et les propriétés utilisées dans les animations.|  
|[Vue d’ensemble des événements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)|Décrit les événements disponibles sur le <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock> objets pour l’exécution de code à des points dans la chronologie, tels que begin, suspendre, reprendre, ignorer ou arrêter.|  
|[Rubriques "Comment"](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)|Contient des exemples de code pour l’utilisation des animations et des chronologies dans votre application.|  
|[Rubriques "Comment" horloges](../../../../docs/framework/wpf/graphics-multimedia/clocks-how-to-topics.md)|Contient des exemples de code pour l’utilisation de la <xref:System.Windows.Media.Animation.Clock> objet dans votre application.|  
|[Rubriques de procédures d’image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)|Contient des exemples de code pour l’utilisation des animations d’image clé dans votre application.|  
|[Rubriques "Comment" Animation de chemin d’accès](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)|Contient des exemples de code pour l’utilisation des animations de tracés dans votre application.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Référence  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>