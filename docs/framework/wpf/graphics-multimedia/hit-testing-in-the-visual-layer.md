---
title: "Test de positionnement dans la couche visuelle | Microsoft Docs"
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
  - "fonctionnalité de test de positionnement"
  - "couche visuelle, fonctionnalité de test de positionnement"
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
caps.latest.revision: 42
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 41
---
# Test de positionnement dans la couche visuelle
Cette rubrique propose une vue d'ensemble de la fonctionnalité de test de positionnement fournie par la couche visuelle.  La prise en charge du test de positionnement vous permet de déterminer si la valeur d'une géométrie ou d'un point tombe dans le contenu rendu d'un <xref:System.Windows.Media.Visual>, ce qui vous permet d'implémenter un comportement d'interface utilisateur tel qu'un rectangle de sélection pour sélectionner plusieurs objets.  
  
   
  
<a name="hit_testing_scenarios"></a>   
## Scénarios de test de positionnement  
 La classe <xref:System.Windows.UIElement> fournit la méthode <xref:System.Windows.UIElement.InputHitTest%2A>, qui vous permet d'effectuer un test de positionnement sur un élément à l'aide d'une valeur de coordonnée donnée.  Dans de nombreux cas, la méthode <xref:System.Windows.UIElement.InputHitTest%2A> propose les fonctionnalités souhaitées pour implémenter un test de positionnement d'éléments.  Cependant, dans plusieurs scénarios, vous devrez peut\-être implémenter le test de positionnement au niveau de la couche visuelle.  
  
-   Test de positionnement sur des objets non <xref:System.Windows.UIElement> : ce scénario est d'application si vous effectuez un test de positionnement sur des objets non <xref:System.Windows.UIElement>, tels que <xref:System.Windows.Media.DrawingVisual> ou des objets graphiques.  
  
-   Test de positionnement à l'aide d'une géométrie : ce scénario s'applique si vous devez effectuer un test de positionnement à l'aide d'un objet de géométrie plutôt que de la valeur de coordonnée d'un point.  
  
-   Test de positionnement sur plusieurs objets : ce scénario est d'application lorsque vous devez effectuer un test de positionnement sur plusieurs objets, tels que des objets chevauchants.  Vous pouvez obtenir des résultats pour tous les visuels croisant une géométrie ou un point, et pas seulement pour le premier.  
  
-   Ignorer la stratégie de test de positionnement <xref:System.Windows.UIElement> : ce scénario est d'application lorsque vous devez ignorer la stratégie de test de positionnement <xref:System.Windows.UIElement>, qui prend en compte des facteurs tels que le fait qu'un élément est désactivé ou invisible.  
  
> [!NOTE]
>  Pour obtenir un exemple de code complet illustrant le test de positionnement sur la couche visuelle, consultez [Test de positionnement à l'aide de DrawingVisuals, exemple](http://go.microsoft.com/fwlink/?LinkID=159994) et [Test de positionnement avec interopérabilité Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## Prise en charge du test de positionnement  
 Le but des méthodes <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> dans la classe <xref:System.Windows.Media.VisualTreeHelper> est de déterminer si la valeur de coordonnée d'une géométrie ou d'un point est comprise dans le contenu rendu d'un objet donné, tel qu'un contrôle ou un élément graphique.  Vous pouvez par exemple utiliser le test de positionnement pour déterminer si un clic de souris dans le rectangle englobant d'un objet tombe dans la géométrie d'un cercle.  Vous pouvez également choisir de substituer l'implémentation par défaut du test de positionnement pour effectuer vos propres calculs de test de positionnement personnalisés.  
  
 L'illustration suivante montre la relation entre la région d'un objet non rectangulaire et son rectangle englobant.  
  
 ![Diagramme de la région de test de positionnement valide](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk\_mmgraphics\_visuals\_hittest\_1")  
Diagramme de la région de test de positionnement valide  
  
<a name="hit_testing_and_z-order"></a>   
## Test de positionnement et ordre de plan  
 La couche visuelle de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prend en charge le test de positionnement sur tous les objets situés sous un point ou une géométrie, et pas seulement sur ceux de premier niveau.  Les résultats sont retournés sous la forme d'un [ordre de plan](GTMT).  L'objet visuel que vous passez en tant que paramètre à la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> détermine toutefois la partie de l'[arborescence visuelle](GTMT) qui sera soumise au test de positionnement.  Vous pouvez effectuer le test de positionnement sur l'intégralité de l'arborescence visuelle ou sur une partie.  
  
 Dans l'illustration suivante, l'objet cercle est à la fois sur le carré et le triangle.  Si vous souhaitez uniquement effectuer le test de positionnement sur l'objet visuel dont la valeur de l'[ordre de plan](GTMT) est de premier niveau, vous pouvez définir l'énumération du test de positionnement visuelle pour qu'elle retourne <xref:System.Windows.Media.HitTestResultBehavior> depuis <xref:System.Windows.Media.HitTestResultCallback> afin d'interrompre le parcours du test de positionnement après le premier élément.  
  
 ![Diagramme de l'ordre de plan d'une arborescence d'éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk\_mmgraphics\_visuals\_hittest\_2")  
Diagramme de l'ordre de plan d'une arborescence visuelle  
  
 Si vous souhaitez énumérer tous les objets visuels situés sous un point ou une géométrie spécifique, retournez <xref:System.Windows.Media.HitTestResultBehavior> depuis <xref:System.Windows.Media.HitTestResultCallback>.  Cela signifie que vous pouvez effectuer un test de positionnement pour des objets visuels situés sous d'autres objets, même s'ils sont complètement masqués.  Consultez l'exemple de code dans la section « Utilisation d'un rappel des résultats du test de positionnement » pour plus d'informations.  
  
> [!NOTE]
>  Un objet visuel transparent peut également faire l'objet d'un test de positionnement.  
  
<a name="using_default_hit_testing"></a>   
## Utilisation du test de positionnement par défaut  
 Vous pouvez déterminer si un point se trouve dans la géométrie d'un objet visuel en utilisant la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pour spécifier un objet visuel et la valeur de coordonnée d'un point sur lesquels effectuer le test.  Le paramètre d'objet visuel identifie le point de départ au sein de l'arborescence visuelle pour la recherche de test de positionnement.  Si un objet visuel dont la géométrie contient la coordonnée est retrouvé dans l'arborescence visuelle, il prend la valeur de la propriété <xref:System.Windows.Media.HitTestResult.VisualHit%2A> d'un objet <xref:System.Windows.Media.HitTestResult>.  L'objet <xref:System.Windows.Media.HitTestResult> est ensuite retourné à partir de la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  Si le point n'est pas contenu dans la sous\-arborescence visuelle sur laquelle vous effectuez le test de positionnement, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> retourne `null`.  
  
> [!NOTE]
>  Le test de positionnement par défaut retourne toujours l'objet de premier niveau dans l'[ordre de plan](GTMT).  Pour identifier tous les objets visuels, y compris ceux masqués partiellement ou totalement, utilisez un rappel des résultats du test de positionnement.  
  
 La valeur de coordonnée que vous passez au paramètre du point pour la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> doit être relative par rapport à l'espace de coordonnées de l'objet visuel qui fait l'objet du test de positionnement.  Par exemple, si vous imbriquez des objets visuels définis à \(100, 100\) dans l'espace de coordonnées du parent, un test de positionnement d'un enfant visuel à \(0, 0\) équivaut à un test de positionnement à \(100, 100\) dans l'espace de coordonnées du parent.  
  
 Le code suivant montre comment configurer des gestionnaires d'événement de souris pour un objet <xref:System.Windows.UIElement> utilisé pour capturer des événements utilisés pour le test de positionnement.  
  
 [!code-csharp[HitTestingOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### Impact de l'arborescence visuelle sur le test de positionnement  
 Le point de départ défini au sein de l'arborescence visuelle détermine les objets retournés lors de l'énumération du test de positionnement des objets.  Si vous effectuez un test de positionnement sur plusieurs objets, l'objet visuel utilisé comme point de départ dans l'arborescence d'éléments visuels doit être l'ancêtre commun de tous les objets en question.  Par exemple, si vous voulez effectuer un test de positionnement de l'élément bouton et du visuel du dessin dans le diagramme suivant, vous devez définir comme point de départ dans l'arborescence visuelle l'ancêtre commun de ces deux objets.  Dans ce cas, l'élément zone de dessin est l'ancêtre commun de l'élément bouton et du visuel du dessin.  
  
 ![Diagramme d'une hiérarchie d'arborescence d'éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-overview-01.png "wcpsdk\_mmgraphics\_visuals\_overview\_01")  
Diagramme d'une hiérarchie d'une arborescence visuelle  
  
> [!NOTE]
>  La propriété <xref:System.Windows.UIElement.IsHitTestVisible%2A> obtient ou définit une valeur qui déclare si un objet dérivé de <xref:System.Windows.UIElement> peut être retourné en tant que résultat de test de positionnement depuis une partie de son contenu rendu.  Cela vous permet de modifier de manière sélective l'arborescence visuelle afin de déterminer les objets visuels concernés par un test de positionnement.  
  
<a name="using_a_hit_test_result_callback"></a>   
## Utilisation d'un rappel des résultats du test de positionnement  
 Vous pouvez énumérer tous les objets visuels d'une arborescence visuelle dont la géométrie contient une valeur de coordonnée spécifiée.  Cela vous permet d'identifier tous les objets visuels, y compris ceux masqués totalement ou partiellement par d'autres.  L'énumération des objets visuels d'une arborescence visuelle fait appel à la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> associée à une fonction de rappel de test de positionnement.  La fonction de rappel de test de positionnement est appelée par le système lorsque la valeur de coordonnée que vous spécifiez est contenue dans un objet visuel.  
  
 Lors de l'énumération des résultats du test de positionnement, vous ne devez effectuer aucune opération modifiant l'arborescence visuelle.  L'ajout ou la suppression d'un objet de l'arborescence visuelle pendant qu'elle est parcourue peut en effet déboucher sur un comportement imprévisible.  Vous pouvez modifier l'arborescence visuelle en toute sécurité après que la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> a été retournée.  Vous pouvez fournir une structure de données, telle qu'une classe <xref:System.Collections.ArrayList>, pour stocker des valeurs lors de l'énumération des résultats du test de positionnement.  
  
 [!code-csharp[HitTestingOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 La méthode de rappel de test de positionnement définit les actions que vous exécutez lorsqu'un test de positionnement est identifié sur un objet visuel particulier dans l'arborescence visuelle.  Après avoir exécuté les actions, vous retournez une valeur <xref:System.Windows.Media.HitTestResultBehavior> qui détermine si l'énumération d'autres objets visuels doit ou non se poursuivre.  
  
 [!code-csharp[HitTestingOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
>  L'énumération des objets visuels atteints se fait selon l'[ordre de plan](GTMT).  L'objet visuel de premier niveau dans l'[ordre de plan](GTMT) est le premier objet énuméré.  Les objets visuels restants sont ensuite énumérés dans l'[ordre de plan](GTMT) décroissant.  Cet ordre d'énumération correspond à l'ordre de rendu des visuels.  
  
 Vous pouvez arrêter l'énumération d'objets visuels à tout moment durant l'exécution de la fonction de rappel de test de positionnement en retournant <xref:System.Windows.Media.HitTestResultBehavior>.  
  
 [!code-csharp[HitTestingOverview#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## Utilisation d'un rappel de filtre du test de positionnement  
 Vous pouvez utiliser un filtre de test de positionnement pour restreindre les objets transmis aux résultats du test de positionnement.  Cela vous permet d'ignorer les parties de l'arborescence visuelle que vous ne souhaitez pas traiter dans vos résultats de test de positionnement.  Pour implémenter un filtre de test de positionnement, vous devez définir une fonction de rappel de filtre du test de positionnement et la passez en tant que valeur de paramètre lorsque vous appelez la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  
  
 [!code-csharp[HitTestingOverview#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Si vous ne souhaitez pas utiliser la fonction de rappel de filtre du test de positionnement, passez la valeur de paramètre `null` pour la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  
  
 [!code-csharp[HitTestingOverview#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Élagage d'une arborescence d'éléments visuels à l'aide d'un filtre de test de positionnement](../../../../docs/framework/wpf/graphics-multimedia/media/filteredvisualtree-01.png "FilteredVisualTree\_01")  
Nettoyage d'une arborescence visuelle  
  
 La fonction de rappel de filtre du test de positionnement vous permet d'énumérer tous les visuels dont le contenu rendu contient les coordonnées que vous spécifiez.  Vous pouvez toutefois choisir d'ignorer certaines branches de l'arborescence visuelle que vous ne voulez pas traiter dans votre fonction de rappel des résultats du test de positionnement.  La valeur de retour de la fonction de rappel du filtre du test de positionnement détermine le type d'action que l'énumération des objets visuels doit prendre.  Par exemple, si vous retournez la valeur, <xref:System.Windows.Media.HitTestFilterBehavior>, vous pouvez supprimer l'objet visuel actuel et ses enfants de l'énumération des résultats du test de positionnement.  Cela signifie que la fonction de rappel des résultats du test de positionnement ne verra pas ces objets dans son énumération.  Le nettoyage de l'arborescence visuelle d'objets diminue le temps du traitement pendant le passe de l'énumération des résultats du test de positionnement.  Dans l'exemple de code suivant, le filtre ignore certaines étiquettes et leurs descendants et effectue un test de positionnement sur tout le reste.  
  
 [!code-csharp[HitTestingOverview#106](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
>  Le rappel de filtre du test de positionnement est parfois appelé lorsque le rappel des résultats du test de positionnement ne l'est pas.  
  
<a name="overriding_default_hit_testing"></a>   
## Substitution du test de positionnement par défaut  
 Vous pouvez substituer la prise en charge du test de positionnement par défaut d'un objet visuel en substituant la méthode <xref:System.Windows.Media.Visual.HitTestCore%2A>.  Cela signifie que lorsque vous appelez la méthode <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>, votre implémentation substituée de <xref:System.Windows.Media.Visual.HitTestCore%2A> est appelée.  Votre méthode substituée est appelée lorsqu'un test de positionnement tombe dans le rectangle englobant de l'objet visuel, même si la coordonnée tombe en dehors du contenu rendu de l'objet visuel.  
  
 [!code-csharp[HitTestingOverview#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Il peut arriver que vous souhaitiez effectuer le test de positionnement en même temps sur le rectangle englobant et le contenu rendu d'un objet visuel.  En utilisant la valeur de paramètre `PointHitTestParameters` dans votre méthode <xref:System.Windows.Media.Visual.HitTestCore%2A> substituée en guise de paramètre pour la méthode de base <xref:System.Windows.Media.Visual.HitTestCore%2A>, vous pouvez effectuer un test de positionnement sur le rectangle englobant d'un objet visuel, puis un deuxième test de positionnement sur le contenu rendu.  
  
 [!code-csharp[HitTestingOverview#108](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## Voir aussi  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>   
 <xref:System.Windows.Media.HitTestResult>   
 <xref:System.Windows.Media.HitTestResultCallback>   
 <xref:System.Windows.Media.HitTestFilterCallback>   
 <xref:System.Windows.UIElement.IsHitTestVisible%2A>   
 [Test de positionnement à l'aide de DrawingVisuals, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159994)   
 [Test de positionnement avec interopérabilité Win32, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159995)   
 [Effectuer un test de positionnement avec Geometry dans un Visual](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)   
 [Effectuer un test de positionnement à l'aide d'un conteneur hôte Win32](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-a-win32-host-container.md)