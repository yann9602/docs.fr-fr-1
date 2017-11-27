---
title: Vue d'ensemble des ornements
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42e37a1a1c00ab1a2039eba5f310cadf9a2175c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="adorners-overview"></a><span data-ttu-id="7c460-102">Vue d'ensemble des ornements</span><span class="sxs-lookup"><span data-stu-id="7c460-102">Adorners Overview</span></span>
<span data-ttu-id="7c460-103">Les ornements sont un type spécial de <xref:System.Windows.FrameworkElement>, utilisés pour fournir des signaux visuels à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7c460-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="7c460-104">Les ornements permettent notamment d’ajouter des descripteurs fonctionnels à des éléments ou de fournir des informations d’état sur un contrôle.</span><span class="sxs-lookup"><span data-stu-id="7c460-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="7c460-105">À propos des ornements</span><span class="sxs-lookup"><span data-stu-id="7c460-105">About Adorners</span></span>  
 <span data-ttu-id="7c460-106">Un <xref:System.Windows.Documents.Adorner> personnalisé <xref:System.Windows.FrameworkElement> qui est lié à un <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7c460-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="7c460-107">Les ornements sont restitués dans un <xref:System.Windows.Documents.AdornerLayer>, qui est une surface de rendu qui est toujours au-dessus de l’élément orné ou une collection d’éléments ornés.</span><span class="sxs-lookup"><span data-stu-id="7c460-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="7c460-108">Le rendu d’un ornement est indépendant du rendu de la <xref:System.Windows.UIElement> qui est lié l’ornement.</span><span class="sxs-lookup"><span data-stu-id="7c460-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="7c460-109">Un ornement est généralement positionné par rapport à l’élément auquel il est lié, au moyen de l’origine des coordonnées 2D standard située dans le coin supérieur gauche de l’élément orné.</span><span class="sxs-lookup"><span data-stu-id="7c460-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="7c460-110">Parmi les applications courantes des ornements, citons les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c460-110">Common applications for adorners include:</span></span>  
  
-   <span data-ttu-id="7c460-111">Ajout de handles fonctionnels à un <xref:System.Windows.UIElement> qui permettent à un utilisateur de manipuler l’élément d’une certaine façon (redimensionner, faire pivoter, repositionner, etc.).</span><span class="sxs-lookup"><span data-stu-id="7c460-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
-   <span data-ttu-id="7c460-112">Retour visuel pour indiquer différents états, ou en réponse à différents événements</span><span class="sxs-lookup"><span data-stu-id="7c460-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
-   <span data-ttu-id="7c460-113">Superposition de décorations visuelles sur un <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7c460-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="7c460-114">Masquage visuel ou remplacer tout ou partie d’un <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7c460-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="7c460-115"> fournit une infrastructure de base pour orner des éléments visuels.</span><span class="sxs-lookup"><span data-stu-id="7c460-115"> provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="7c460-116">Le tableau suivant répertorie les principaux types utilisés pour orner des objets et leur but.</span><span class="sxs-lookup"><span data-stu-id="7c460-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="7c460-117">Plusieurs exemples d’utilisation suivent.</span><span class="sxs-lookup"><span data-stu-id="7c460-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="7c460-118">Classe de base abstraite à partir de laquelle toutes les implémentations d’ornement concrètes sont héritées.</span><span class="sxs-lookup"><span data-stu-id="7c460-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="7c460-119">Classe représentant une couche de rendu pour le ou les ornements d’un ou plusieurs éléments ornés.</span><span class="sxs-lookup"><span data-stu-id="7c460-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="7c460-120">Classe permettant d’associer une couche d’ornement à une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="7c460-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="7c460-121">Implémentation d’un ornement personnalisé</span><span class="sxs-lookup"><span data-stu-id="7c460-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="7c460-122">L’infrastructure des ornements fournie par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est principalement destinée à prendre en charge la création d’ornements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7c460-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="7c460-123">Un ornement personnalisé est créé en implémentant une classe qui hérite de l’abstraite <xref:System.Windows.Documents.Adorner> classe.</span><span class="sxs-lookup"><span data-stu-id="7c460-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c460-124">Le parent d’un <xref:System.Windows.Documents.Adorner> est la <xref:System.Windows.Documents.AdornerLayer> qui restitue le <xref:System.Windows.Documents.Adorner>, pas l’élément orné.</span><span class="sxs-lookup"><span data-stu-id="7c460-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="7c460-125">L’exemple suivant montre une classe qui implémente un ornement simple.</span><span class="sxs-lookup"><span data-stu-id="7c460-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="7c460-126">L’ornement d’exemple orne simplement les angles d’un <xref:System.Windows.UIElement> avec des cercles.</span><span class="sxs-lookup"><span data-stu-id="7c460-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="7c460-127">L’illustration suivante montre le SimpleCircleAdorner appliqué à un <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7c460-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="7c460-128">![Exemple d’ornements : zone de texte ornée](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span><span class="sxs-lookup"><span data-stu-id="7c460-128">![Adorners Example: An adorned TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span></span>  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="7c460-129">Comportement de rendu des ornements</span><span class="sxs-lookup"><span data-stu-id="7c460-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="7c460-130">Il est important de noter que les ornements n’incluent aucun comportement de rendu inhérent ; il appartient donc à l’implémenteur d’un ornement de vérifier son rendu.</span><span class="sxs-lookup"><span data-stu-id="7c460-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="7c460-131">Une méthode courante de l’implémentation du comportement de rendu consiste à remplacer le <xref:System.Windows.UIElement.OnRender%2A> méthode et l’utilisation d’un ou plusieurs <xref:System.Windows.Media.DrawingContext> objets pour restituer les visuels de l’ornement en fonction des besoins (comme indiqué dans l’exemple ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="7c460-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c460-132">Tout ce que vous placez dans la couche d’ornement s’affiche au dessus de tous les styles que vous avez définis.</span><span class="sxs-lookup"><span data-stu-id="7c460-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="7c460-133">En d’autres termes, les ornements sont toujours visuellement en haut et ne peuvent pas être substitués à l’aide de l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="7c460-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="7c460-134">Événements et test de positionnement</span><span class="sxs-lookup"><span data-stu-id="7c460-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="7c460-135">Les ornements reçoivent des événements d’entrée comme n’importe quel autre <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="7c460-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="7c460-136">Un ornement ayant toujours un ordre de plan supérieur à l’élément qu’il ornemente, l’ornement reçoit des événements d’entrée (tel que <xref:System.Windows.UIElement.Drop> ou <xref:System.Windows.UIElement.MouseMove>) qui peuvent être prévus pour l’élément ornementé sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="7c460-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="7c460-137">Un ornement peut écouter certains événements d’entrée et les passer à l’élément orné sous-jacent en déclenchant à nouveau l’événement.</span><span class="sxs-lookup"><span data-stu-id="7c460-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="7c460-138">Pour activer le test de positionnement direct d’éléments sous un ornement, définissez le test de positionnement <xref:System.Windows.UIElement.IsHitTestVisible%2A> propriété **false** sur l’ornement.</span><span class="sxs-lookup"><span data-stu-id="7c460-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="7c460-139">Pour plus d’informations sur le test de positionnement, consultez</span><span class="sxs-lookup"><span data-stu-id="7c460-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="7c460-140">[Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="7c460-140">[Hit Testing in the Visual Layer](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="7c460-141">Ornementation d’un UIElement unique</span><span class="sxs-lookup"><span data-stu-id="7c460-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="7c460-142">Pour lier un ornement à un emplacement donné <xref:System.Windows.UIElement>, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7c460-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7c460-143">Appelez la méthode statique <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour obtenir un <xref:System.Windows.Documents.AdornerLayer> de l’objet pour le <xref:System.Windows.UIElement> à orner.</span><span class="sxs-lookup"><span data-stu-id="7c460-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="7c460-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>parcourt l’arborescence d’éléments visuels, en commençant à la position spécifiée <xref:System.Windows.UIElement>et retourne la première couche d’ornement qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="7c460-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="7c460-145">(Si aucune couche d’ornement n’est trouvée, la méthode retourne Null.)</span><span class="sxs-lookup"><span data-stu-id="7c460-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="7c460-146">Appelez le <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode à laquelle lier l’ornement à la cible <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7c460-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="7c460-147">L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) pour un <xref:System.Windows.Controls.TextBox> nommé *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="7c460-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="7c460-148">L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="7c460-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="7c460-149">Ornementation des enfants d’un panneau</span><span class="sxs-lookup"><span data-stu-id="7c460-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="7c460-150">Pour lier un ornement aux enfants d’un <xref:System.Windows.Controls.Panel>, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7c460-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7c460-151">Appelez le `static` méthode <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour rechercher une couche d’ornement pour l’élément dont les enfants doivent être ornés.</span><span class="sxs-lookup"><span data-stu-id="7c460-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="7c460-152">Énumérez les enfants de l’élément parent et appelez le <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier un ornement à chaque élément enfant.</span><span class="sxs-lookup"><span data-stu-id="7c460-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="7c460-153">L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) pour les enfants d’un <xref:System.Windows.Controls.StackPanel> nommé *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="7c460-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="7c460-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c460-154">See Also</span></span>  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [<span data-ttu-id="7c460-155">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="7c460-155">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="7c460-156">Peinture avec des images, des dessins et des objets visuels</span><span class="sxs-lookup"><span data-stu-id="7c460-156">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="7c460-157">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="7c460-157">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="7c460-158">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="7c460-158">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
