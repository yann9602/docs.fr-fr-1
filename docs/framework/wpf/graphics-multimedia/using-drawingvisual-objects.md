---
title: Utilisation d'objets DrawingVisual
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
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a33e56b69a357694a1d1a23d5cd3c887c88cea37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-drawingvisual-objects"></a><span data-ttu-id="8732f-102">Utilisation d'objets DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="8732f-102">Using DrawingVisual Objects</span></span>
<span data-ttu-id="8732f-103">Cette rubrique fournit une vue d’ensemble de l’utilisation de <xref:System.Windows.Media.DrawingVisual> des objets dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] couche visuelle.</span><span class="sxs-lookup"><span data-stu-id="8732f-103">This topic provides an overview of how to use <xref:System.Windows.Media.DrawingVisual> objects in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual layer.</span></span>  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a><span data-ttu-id="8732f-104">Objet DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="8732f-104">DrawingVisual Object</span></span>  
 <span data-ttu-id="8732f-105">Le <xref:System.Windows.Media.DrawingVisual> est une classe qui est utilisé pour restituer le texte, des images ou des formes de dessin légère.</span><span class="sxs-lookup"><span data-stu-id="8732f-105">The <xref:System.Windows.Media.DrawingVisual> is a lightweight drawing class that is used to render shapes, images, or text.</span></span> <span data-ttu-id="8732f-106">Cette classe est dite légère, car elle n’assure pas la gestion des dispositions ni des événements, ce qui améliore ses performances.</span><span class="sxs-lookup"><span data-stu-id="8732f-106">This class is considered lightweight because it does not provide layout or event handling, which improves its performance.</span></span> <span data-ttu-id="8732f-107">C’est pourquoi, les dessins de ce type sont idéaux pour les arrière-plans et les images clipart.</span><span class="sxs-lookup"><span data-stu-id="8732f-107">For this reason, drawings are ideal for backgrounds and clip art.</span></span>  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a><span data-ttu-id="8732f-108">Conteneur hôte DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="8732f-108">DrawingVisual Host Container</span></span>  
 <span data-ttu-id="8732f-109">Pour pouvoir utiliser <xref:System.Windows.Media.DrawingVisual> des objets, vous devez créer un conteneur d’hôte pour les objets.</span><span class="sxs-lookup"><span data-stu-id="8732f-109">In order to use <xref:System.Windows.Media.DrawingVisual> objects, you need to create a host container for the objects.</span></span> <span data-ttu-id="8732f-110">L’objet conteneur hôte doit dériver de la <xref:System.Windows.FrameworkElement> (classe), qui fournit la disposition et la gestion des événements qui le prennent en charge le <xref:System.Windows.Media.DrawingVisual> ne contient pas de classe.</span><span class="sxs-lookup"><span data-stu-id="8732f-110">The host container object must derive from the <xref:System.Windows.FrameworkElement> class, which provides the layout and event handling support that the <xref:System.Windows.Media.DrawingVisual> class lacks.</span></span> <span data-ttu-id="8732f-111">L’objet de type conteneur hôte n’affiche pas de propriétés visibles, dans la mesure où son but principal est de contenir des objets enfants.</span><span class="sxs-lookup"><span data-stu-id="8732f-111">The host container object does not display any visible properties, since its main purpose is to contain child objects.</span></span> <span data-ttu-id="8732f-112">Toutefois, le <xref:System.Windows.UIElement.Visibility%2A> propriété du conteneur hôte doit être définie sur <xref:System.Windows.Visibility.Visible>; sinon, aucun de ses éléments enfants seront visibles.</span><span class="sxs-lookup"><span data-stu-id="8732f-112">However, the <xref:System.Windows.UIElement.Visibility%2A> property of the host container must be set to <xref:System.Windows.Visibility.Visible>; otherwise, none of its child elements will be visible.</span></span>  
  
 <span data-ttu-id="8732f-113">Lorsque vous créez un objet de conteneur d’hôte pour des objets visuels, vous devez stocker les références d’objet visuel dans un <xref:System.Windows.Media.VisualCollection>.</span><span class="sxs-lookup"><span data-stu-id="8732f-113">When you create a host container object for visual objects, you need to store the visual object references in a <xref:System.Windows.Media.VisualCollection>.</span></span> <span data-ttu-id="8732f-114">Utilisez la <xref:System.Windows.Media.VisualCollection.Add%2A> méthode pour ajouter un objet visuel pour le conteneur d’hôte.</span><span class="sxs-lookup"><span data-stu-id="8732f-114">Use the <xref:System.Windows.Media.VisualCollection.Add%2A> method to add a visual object to the host container.</span></span> <span data-ttu-id="8732f-115">Dans l’exemple suivant, un objet conteneur hôte est créé et trois objets visuels sont ajoutés à ses <xref:System.Windows.Media.VisualCollection>.</span><span class="sxs-lookup"><span data-stu-id="8732f-115">In the following example, a host container object is created, and three visual objects are added to its <xref:System.Windows.Media.VisualCollection>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  <span data-ttu-id="8732f-116">Pour consulter l’intégralité de l’exemple de code duquel l’exemple de code précédent a été extrait, référez-vous à la section [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994) (Test de positionnement à l’aide d’exemples de DrawingVisuals).</span><span class="sxs-lookup"><span data-stu-id="8732f-116">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994).</span></span>  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a><span data-ttu-id="8732f-117">Création d'objets DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="8732f-117">Creating DrawingVisual Objects</span></span>  
 <span data-ttu-id="8732f-118">Lorsque vous créez un <xref:System.Windows.Media.DrawingVisual> de l’objet, il n’a aucun contenu de dessin.</span><span class="sxs-lookup"><span data-stu-id="8732f-118">When you create a <xref:System.Windows.Media.DrawingVisual> object, it has no drawing content.</span></span> <span data-ttu-id="8732f-119">Vous pouvez ajouter du texte, de graphiques ou de contenu de l’image en récupérant l’objet <xref:System.Windows.Media.DrawingContext> et de dessin dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="8732f-119">You can add text, graphics, or image content by retrieving the object's <xref:System.Windows.Media.DrawingContext> and drawing into it.</span></span> <span data-ttu-id="8732f-120">A <xref:System.Windows.Media.DrawingContext> est retourné en appelant le <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> méthode d’un <xref:System.Windows.Media.DrawingVisual> objet.</span><span class="sxs-lookup"><span data-stu-id="8732f-120">A <xref:System.Windows.Media.DrawingContext> is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span>  
  
 <span data-ttu-id="8732f-121">Pour dessiner un rectangle dans le <xref:System.Windows.Media.DrawingContext>, utilisez le <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> méthode de la <xref:System.Windows.Media.DrawingContext> objet.</span><span class="sxs-lookup"><span data-stu-id="8732f-121">To draw a rectangle into the <xref:System.Windows.Media.DrawingContext>, use the <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> method of the <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="8732f-122">Il existe des méthodes similaires pour dessiner d’autres types de contenu.</span><span class="sxs-lookup"><span data-stu-id="8732f-122">Similar methods exist for drawing other types of content.</span></span> <span data-ttu-id="8732f-123">Quand vous avez terminé le contenu de dessin dans le <xref:System.Windows.Media.DrawingContext>, appelez le <xref:System.Windows.Media.DrawingContext.Close%2A> méthode pour fermer le <xref:System.Windows.Media.DrawingContext> et conserver le contenu.</span><span class="sxs-lookup"><span data-stu-id="8732f-123">When you are finished drawing content into the <xref:System.Windows.Media.DrawingContext>, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the <xref:System.Windows.Media.DrawingContext> and persist the content.</span></span>  
  
 <span data-ttu-id="8732f-124">Dans l’exemple suivant, un <xref:System.Windows.Media.DrawingVisual> objet est créé et un rectangle est dessiné dans son <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="8732f-124">In the following example, a <xref:System.Windows.Media.DrawingVisual> object is created, and a rectangle is drawn into its <xref:System.Windows.Media.DrawingContext>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a><span data-ttu-id="8732f-125">Création de remplacements pour les membres FrameworkElement</span><span class="sxs-lookup"><span data-stu-id="8732f-125">Creating Overrides for FrameworkElement Members</span></span>  
 <span data-ttu-id="8732f-126">L’objet de type conteneur hôte est chargé de gérer sa collection d’objets visuels.</span><span class="sxs-lookup"><span data-stu-id="8732f-126">The host container object is responsible for managing its collection of visual objects.</span></span> <span data-ttu-id="8732f-127">Cela nécessite que le conteneur d’hôte implémenter des substitutions de membres pour dérivé <xref:System.Windows.FrameworkElement> classe.</span><span class="sxs-lookup"><span data-stu-id="8732f-127">This requires that the host container implement member overrides for the derived <xref:System.Windows.FrameworkElement> class.</span></span>  
  
 <span data-ttu-id="8732f-128">La liste suivante décrit les deux membres que vous devez substituer :</span><span class="sxs-lookup"><span data-stu-id="8732f-128">The following list describes the two members you must override:</span></span>  
  
-   <span data-ttu-id="8732f-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Retourne un enfant à l’index spécifié de la collection d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="8732f-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Returns a child at the specified index from the collection of child elements.</span></span>  
  
-   <span data-ttu-id="8732f-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Obtient le nombre d’éléments enfants visuels dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="8732f-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Gets the number of visual child elements within this element.</span></span>  
  
 <span data-ttu-id="8732f-131">Dans l’exemple suivant, les remplacements pour les deux <xref:System.Windows.FrameworkElement> membres sont implémentées.</span><span class="sxs-lookup"><span data-stu-id="8732f-131">In the following example, overrides for the two <xref:System.Windows.FrameworkElement> members are implemented.</span></span>  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a><span data-ttu-id="8732f-132">Prise en charge du test de positionnement</span><span class="sxs-lookup"><span data-stu-id="8732f-132">Providing Hit Testing Support</span></span>  
 <span data-ttu-id="8732f-133">L’objet conteneur hôte peut fournir la gestion des événements même si elle n’affiche pas de propriétés visibles, toutefois, son <xref:System.Windows.UIElement.Visibility%2A> propriété doit être définie sur <xref:System.Windows.Visibility.Visible>.</span><span class="sxs-lookup"><span data-stu-id="8732f-133">The host container object can provide event handling even if it does not display any visible properties—however, its <xref:System.Windows.UIElement.Visibility%2A> property must be set to <xref:System.Windows.Visibility.Visible>.</span></span> <span data-ttu-id="8732f-134">Cela vous permet de créer une routine de gestion des événements pour le conteneur hôte, capable de détecter les événements de la souris, tels que le relâchement du bouton gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="8732f-134">This allows you to create an event handling routine for the host container that can trap mouse events, such as the release of the left mouse button.</span></span> <span data-ttu-id="8732f-135">Routine de gestion d’événements peuvent ensuite implémenter un test de positionnement en appelant le <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="8732f-135">The event handling routine can then implement hit testing by invoking the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="8732f-136">La méthode <xref:System.Windows.Media.HitTestResultCallback> paramètre fait référence à une procédure définie par l’utilisateur que vous pouvez utiliser pour déterminer l’action résultante d’un test de positionnement.</span><span class="sxs-lookup"><span data-stu-id="8732f-136">The method's <xref:System.Windows.Media.HitTestResultCallback> parameter refers to a user-defined procedure that you can use to determine the resulting action of a hit test.</span></span>  
  
 <span data-ttu-id="8732f-137">Dans l’exemple suivant, la prise en charge du test de positionnement est implémentée pour l’objet de type conteneur hôte et ses enfants.</span><span class="sxs-lookup"><span data-stu-id="8732f-137">In the following example, hit testing support is implemented for the host container object and its children.</span></span>  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="8732f-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8732f-138">See Also</span></span>  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [<span data-ttu-id="8732f-139">Vue d’ensemble du rendu graphique de WPF</span><span class="sxs-lookup"><span data-stu-id="8732f-139">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="8732f-140">Test de positionnement dans la couche visuelle</span><span class="sxs-lookup"><span data-stu-id="8732f-140">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
